<template>
  <div>
    <BackgroundStars></BackgroundStars>
    <v-app dark>
      <DefaultHeader></DefaultHeader>

      <v-content>
        <v-container>
          <nuxt></nuxt>
        </v-container>
      </v-content>

      <v-footer :fixed="fixed" app>
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
        headTitles: [
          {
            icon: 'apps',
            title: 'Welcome',
            to: '/'
          },
          {
            icon: 'bubble_chart',
            title: 'Inspire',
            to: '/inspire'
          },
          {
            icon: 'bubble_chart',
            title: 'detail',
            to: '/detail'
          }
        ],
        items: [
          {
            icon: 'apps',
            title: 'Welcome',
            to: '/'
          },
          {
            icon: 'bubble_chart',
            title: 'Inspire',
            to: '/inspire'
          },
          {
            icon: 'bubble_chart',
            title: 'detail',
            to: '/detail'
          }
        ],
        miniVariant: false,
        right: true,
        title: 'Vuetify.js'
      }
    }
  }
</script>
