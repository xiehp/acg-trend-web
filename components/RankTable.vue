<template>
  <div>
    <v-data-table
      :headers="headers"
      :items="tableData"
      class="elevation-2"
    >
      <template slot="items" slot-scope="props">
        <td class="text-sm-left">
          {{ props.item.no }}
        </td>
        <td class="text-sm-left">
          {{ props.item.name }}
        </td>
        <td class="text-sm-left">
          {{ props.item.playCount }}
        </td>
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
