<template>
  <section class="container">
    <div>
      <logo />
      <h1 class="title">
        acg-trend-web
      </h1>
      <h2 class="subtitle">
        detail
      </h2>
      <div class="links">
        <a href="https://nuxtjs.org/" target="_blank" class="button--green">
          Documentation
        </a>
      </div>
      <div>
        <RankTable :headers="headers" :desserts="desserts1" />
      </div>
      <div>
        <RankTable2 :data="data" />
      </div>

      <v-app id="inspire">
        <div class="text-xs-center">
          <v-btn fab dark small color="primary">
            <v-icon pink>
              remove
            </v-icon>
          </v-btn>

          <v-btn fab dark small color="pink">
            <v-icon dark>
              favorite
            </v-icon>
          </v-btn>

          <v-btn fab dark color="indigo">
            <v-icon dark>
              add
            </v-icon>
          </v-btn>

          <v-btn fab dark color="teal">
            <v-icon dark>
              list
            </v-icon>
          </v-btn>

          <v-btn fab dark large color="cyan">
            <v-icon dark>
              edit
            </v-icon>
          </v-btn>

          <v-btn fab dark large color="purple">
            <v-icon dark>
              android
            </v-icon>
          </v-btn>
        </div>
      </v-app>
      <div>
        <v-btn color="success">
          Success
        </v-btn>
        <v-btn color="error">
          Error
        </v-btn>
        <v-btn color="warning">
          Warning
        </v-btn>
        <v-btn color="info">
          Info
        </v-btn>
      </div>
    </div>
  </section>
</template>

<script>
  import axios from "axios"
  import Logo from "../components/Logo.vue"
  import RankTable from "../components/RankTable.vue"
  import RankTable2 from "../components/RankTable2.vue"

  let rankData;
  let nameSiteMap;

  export default {
    components: {
      Logo,
      RankTable,
      RankTable2,
    },
    asyncData() {
      const url = process.env.baseUrl + "/rank/playData";
      const bbb = axios.get(url)
        .then((res) => {
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

          const nowRankArray = [];
          let index = 1;
          for (const key in nameSiteMap) {
            const nowPlayCount = nameSiteMap[key].all.nowPlayCount;
            if (nowPlayCount == null) {
              continue;
            }
            const obj = {};
            // obj.set("no", ++index);
            // obj.set("name", key);
            // obj.set("playCount", nowPlayCount);
            obj.no = index++;
            obj.name = key;
            obj.playCount = nowPlayCount;
            nowRankArray.push(obj);
          }
          console.log("nowRankArray:" + nowRankArray.length);
          // console.log(res.data.chartName);

          // 构造rank数据
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
          const desserts = [{
            no: "Frozen Yogurt",
            name: 159,
            playCount: 6.0,
          }];
          const desserts1 = nowRankArray;
          // console.log(desserts1);

          return {
            data: result.data,
            headers: headers,
            desserts1: desserts1,
          }
        })
        .catch((e) => {
          console.log(e);
          error({statusCode: 404, message: "Post not found"})
        });
      console.log(bbb);
      return bbb;
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
