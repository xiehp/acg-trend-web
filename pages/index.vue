<template>
  <v-layout row wrap>
    <v-flex v-for="(tableData, key) in tableDatas" :key="key" xs12 sm12 md6>
      <v-card>
        <v-toolbar>
          <v-toolbar-title>{{playCountTitles[key]}}</v-toolbar-title>
          <v-spacer></v-spacer>
        </v-toolbar>
        <RankTable :headers="headers" :table-data="tableData" />
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
  import axios from "axios"
  import RankTable from "../components/RankTable.vue"
  const playCountKeys = ["nowPlayCount", "preHourPlayCount", "preDayPlayCount", "preWeekPlayCount", "preMonthPlayCount", "preYearPlayCount"];
  const playCountTitles = ["当前播放量", "当时播放增长量", "当天播放增长量", "当周播放增长量", "当月播放增长量", "当年播放增长量"];

  const headers = [
    {
      text: "排名",
      align: "left",
      sortable: false,
      value: "no"
    },
    {text: "名称", value: "name"},
    {text: "播放量", value: "playCount"},
  ];

  let rankData;
  let nameSiteMap;

  export default {
    components: {
      RankTable,
    },
    asyncData() {
      const url = process.env.baseUrl + "/rank/playData";
      const tableDatasPM = axios.get(url).then((res) => {
        const result = res.data;
        rankData = result.data;
        nameSiteMap = rankData.nameSiteMap;

        console.log("access url:" + url + " success.");
        // console.log("result size:" + result.length);
        // console.log("rankData:" + rankData);
        // console.log("nameSiteMap:" + nameSiteMap);
        // console.log("result:" + result);
        // console.log("result.name:" + nameSiteMap["3月的狮子 第二季"].all.name);
        // console.log("result length:" + nameSiteMap.length);

        // 构造rank数据

        function convertToTableData(playCountKey) {
          const rankArray = [];
          let index = 1;
          for (const key in nameSiteMap) {
            const playCount = nameSiteMap[key].all[playCountKey];
            if (playCount == null) {
              continue;
            }
            const obj = {};
            // obj.set("no", ++index);
            // obj.set("name", key);
            // obj.set("playCount", playCount);
            obj.no = index++;
            obj.name = key;
            obj.playCount = playCount;
            rankArray.push(obj);
          }
          console.log("RankArray of " + playCountKey + ": " + rankArray.length);

          // console.log(tableData);

          return rankArray;
        }

        console.log(playCountKeys);
        const tableDatas = [];
        for (const key in playCountKeys) {
          const tableDataResult = convertToTableData(playCountKeys[key]);
          tableDatas.push(tableDataResult);
        }
        console.log("axios:");
        // console.log(tableDatas);
        return {tableDatas: tableDatas, headers: headers, playCountTitles: playCountTitles};
      }).catch((e) => {
        console.log(e);
        error({statusCode: 404, message: "Post not found"})
      });

      console.log("asyncData:");
      // console.log(tableDatasPM);
      return tableDatasPM;
    }
  }
  // https://acgtrend.com/detail/trend/data/937/2
  // http://localhost:13002/rank/playData
</script>

<style>
  .container {
    margin: 0 auto;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
  }

  .title {
    font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
    display: block;
    font-weight: 300;
    font-size: 100px;
    color: #35495e;
    letter-spacing: 1px;
  }

  .subtitle {
    font-weight: 300;
    font-size: 42px;
    color: #526488;
    word-spacing: 5px;
    padding-bottom: 15px;
  }

  .links {
    padding-top: 15px;
  }
</style>
