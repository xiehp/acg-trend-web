<template>
  <div>
    <v-toolbar :clipped-left="clipped" fixed app>
      <v-toolbar-title v-text="title"></v-toolbar-title>
      <v-btn to="/">首页</v-btn>
      <v-btn to="/hot">当前热播</v-btn>
<!--      <v-btn to="/BanPlayCount">动画播放量排行</v-btn>-->
      <v-btn to="/PlayCountRankByTime">分时播放量前100排行</v-btn>
      <v-btn to="/AllPlayCount">所有播放量排行</v-btn>
      <v-btn v-if="isLocalhost" to="/detail">detail</v-btn>
      <v-btn v-if="isLocalhost" to="/help">help</v-btn>
      <!--<v-btn icon @click.stop="clipped = !clipped">-->
      <!--<v-icon>web</v-icon>-->
      <!--</v-btn>-->
      <!--<v-btn icon @click.stop="fixed = !fixed">-->
      <!--<v-icon>remove</v-icon>-->
      <!--</v-btn>-->
    </v-toolbar>
  </div>
</template>

<script>
  import {VCard, VToolbar} from 'vuetify/lib';

  export default {
    components: {VCard, VToolbar},
    data() {
      // 调试用按钮
      let isLocalhost = false;
      const url = process.env.baseUrl + this.$route.path;
      console.info("now process.env.baseUrl:" + url);
      if (url != null && url.indexOf("localhost") > -1) {
        isLocalhost = true;
      }

      return {
        title: "河外趋势",
        clipped: false,
        drawer: false,
        fixed: false,
        headTitles: [
          {
            icon: "apps",
            title: "Welcome",
            to: "/"
          },
          {
            icon: "bubble_chart",
            title: "Inspire",
            to: "/inspire"
          },
          {
            icon: "bubble_chart",
            title: "detail",
            to: "/detail"
          }
        ],
        isLocalhost: isLocalhost
      }
    }
  }
</script>
