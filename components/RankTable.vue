<template>
  <div>
    <v-data-table
      :headers="headers"
      :items="desserts"
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
      desserts: Array,
    },
    // data() {
    //   return {
    //     // data2: data,
    //     headers: [
    //       {
    //         text: "Dessert (100g serving)",
    //         align: "left",
    //         sortable: false,
    //         value: "name"
    //       },
    //       {text: "Calories", value: "calories"},
    //       {text: "Fat (g)", value: "fat"},
    //       {text: "Carbs (g)", value: "carbs"},
    //       {text: "Protein (g)", value: "protein"},
    //       {text: "Iron (%)", value: "iron"},
    //     ],
    //     desserts: [
    //       {
    //         name: "Frozen Yogurt",
    //         calories: 159,
    //         fat: 6.0,
    //         carbs: 24,
    //         protein: 4.0,
    //         iron: "1%"
    //       }
    //     ]
    //   }
    // }
  }
  console.log("end RankTable.vue");
</script>

<style scoped>
</style>
