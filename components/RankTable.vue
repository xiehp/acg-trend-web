<template>
  <div>
    <v-data-table
      :headers="headers"
      :items="tableData"
      hide-actions
      class="elevation-2"
    >
      <template v-slot:items="{item}">
        <td class="text-sm-left">
          {{ item.no }}
        </td>
        <td class="text-sm-left">
          {{ item.name }}
        </td>
        <td class="text-sm-left">
          {{ item.playCount }}
        </td>
      </template>

      <template v-slot:no-data>
        <!--<v-alert :value="true" color="error" icon="warning">-->
        对不起，没有数据
        <!--</v-alert>-->
      </template>
    </v-data-table>
  </div>
</template>

<script>
  export default {
    name: "RankTable",
    props: {
      data: Object,
      headers: Array,
      tableData: Array,
    },
  }
  console.log("end RankTable.vue");
</script>

<style scoped>
</style>
