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
        <a-button> Hello world! </a-button>
      </div>
      <div>
        <RankTable />
      </div>

      <v-app id="inspire">
        <div class="text-xs-center">
          <v-btn fab dark small color="primary">
            <v-icon pink>remove</v-icon>
          </v-btn>

          <v-btn fab dark small color="pink">
            <v-icon dark>favorite</v-icon>
          </v-btn>

          <v-btn fab dark color="indigo">
            <v-icon dark>add</v-icon>
          </v-btn>

          <v-btn fab dark color="teal">
            <v-icon dark>list</v-icon>
          </v-btn>

          <v-btn fab dark large color="cyan">
            <v-icon dark>edit</v-icon>
          </v-btn>

          <v-btn fab dark large color="purple">
            <v-icon dark>android</v-icon>
          </v-btn>
        </div>
      </v-app>
      <div>
        <v-btn color="success">Success</v-btn>
        <v-btn color="error">Error</v-btn>
        <v-btn color="warning">Warning</v-btn>
        <v-btn color="info">Info</v-btn>
      </div>
    </div>
  </section>
</template>

<script>
import Logo from '~/components/Logo.vue';
import RankTable from '~/components/RankTable.vue';

export default {
  "components": {
    Logo,
    RankTable
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
