<template>
  <div id="layout_default">
    <v-app dark>
      <BackgroundStars></BackgroundStars>

      <DefaultHeader></DefaultHeader>

      <v-content>
        <v-container>
          <nuxt></nuxt>
        </v-container>
      </v-content>

      <v-footer :fixed="fixed" app style="text-align: center;">
        <span>&copy; 2019</span>
      </v-footer>
    </v-app>
  </div>
</template>

<script>
  import BackgroundStars from "../components/BackgroundStars/BackgroundStars";
  import DefaultHeader from "../components/layout/DefaultHeader.vue";

  export default {
    components: {
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
