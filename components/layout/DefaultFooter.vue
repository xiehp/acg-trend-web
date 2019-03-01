<template>
  <div>
    <v-toolbar :clipped-left="clipped" fixed app>
      <v-toolbar-title v-text="title" />
      <v-btn to="/">home</v-btn>
      <v-btn to="/detail">detail</v-btn>
      <v-btn to="/help">help</v-btn>
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
  export default {
    components: {},
    data() {
      return {
        title: "a title",
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
      }
    }
  }
</script>
