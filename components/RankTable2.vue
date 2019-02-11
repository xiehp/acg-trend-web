<template>
  <div>
    <div>
      aaaaaa
    </div>
    <div>
      {{ title }}
    </div>
    <div>
      <!--{{ data.chartName }}-->
    </div>
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    // asyncData({params}) {
    //   return axios.get(`https://api.coindesk.com/v1/bpi/currentprice.json`)
    //     .then((res) => {
    //       console.log(res);
    //       // return {title: res.data.chartName}
    //       return {title: 'aaa'};
    //     })
    //     .catch(res) {
    //
    //     }
    // }
    asyncData() {
      const bbb = axios.get(`https://api.coindesk.com/v1/bpi/currentprice.json`)
        .then((res) => {
          console.log('res:');
          console.log(res);
          console.log(res.data.chartName)
          return {title: res.data.chartName}
        })
        .catch((e) => {
          console.log(e);
          error({statusCode: 404, message: 'Post not found'})
        })
      console.log(bbb)
      return bbb;
    },
    props: {
      data: Object
    },
    data() {
      return {title: 'defaultTitle'};
    }
    // async asyncData({params}) {
    //   let {data} = await axios.get(`https://api.coindesk.com/v1/bpi/currentprice.json`)
    //   console.log("data:");
    //   console.log(data);
    //   console.log(data.chartName)
    //   return {title: data.chartName}
    // }
    // data() {
    //   let res = {data: {}};
    //   res.data = {title: 'aaa'};
    //   console.log("res:");
    //   console.log(res);
    //   return res.data;
    // }
  }
  console.log('end scritp')
</script>

<style scoped>
</style>
