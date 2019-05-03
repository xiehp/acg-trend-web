<template>
  <div id="layout_default">
    <v-app dark>
      <BackgroundStars></BackgroundStars>

      <DefaultHeader></DefaultHeader>

      <v-content>
        <v-container>
          <nuxt />
        </v-container>
      </v-content>

      <v-footer :fixed="fixed" app style="text-align: center;">
        <span>&copy; 2019</span>
      </v-footer>

      <BaiduTongji />
    </v-app>
  </div>
</template>

<script>
  import BackgroundStars from "../components/BackgroundStars/BackgroundStars";
  import DefaultHeader from "../components/layout/DefaultHeader.vue";
  import BaiduTongji from "../components/BaiduTongji.vue";

  export default {
    components: {
      BaiduTongji,
      BackgroundStars,
      DefaultHeader,
    },
    data() {
      return {
        clipped: false,
        drawer: false,
        fixed: false,
        miniVariant: false,
        right: true,
      }
    }
  }
</script>
