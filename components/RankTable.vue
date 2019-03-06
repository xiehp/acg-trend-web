<template xmlns:v-slot="http://www.w3.org/1999/XSL/Transform">
  <div>
    <v-data-table
      :headers="headers"
      :items="tableData"
      hide-actions
      class="elevation-1"
      :pagination.sync="pagination"
      :loading="true"
      rows-per-page-text=""
      :search="search"
    >
      <template v-slot:items="{item}">
        <td class="text-sm-center">
          {{ item.no }}
        </td>
        <td class="text-sm-left">
          {{ item.name }}
        </td>
        <!--<td class="text-sm-left">-->
        <!--{{ tableData.isNowPlayCount ? item.playCount : item.playCountDiff }}-->
        <!--</td>-->
        <td class="text-sm-right" nowrap>
          {{ item.playCount/10000 }}万
        </td>
        <td class="text-sm-right">
          {{ item.playCountDiff }}
        </td>
      </template>

      <template v-slot:no-data="tableData">
        <!--<v-alert :value="true" color="error" icon="warning">-->
        对不起，没有数据
        <!--</v-alert>-->
      </template>
    </v-data-table>
    <div class="text-xs-center pt-2">
      <v-pagination v-model="pagination.page" :length="pages" />
    </div>
  </div>
</template>

<script>
  export default {
    name: "RankTable",
    props: {
      data: {
        type: Object,
        default: () => {
          return {}
        }
      },
      headers: {
        type: Array,
        default: () => {
          return [];
        }
      },
      tableData: {
        type: Array,
        default: () => {
          const tableData = [];
          tableData.name = "blank";
          tableData.isNowPlayCount = false;
          return tableData;
        }
      },
      search: String,
    },
    data() {
      return {
        pagination: {
          descending: true,
          // page: 0,
          rowsPerPage: 10, // -1 for All
          // sortBy: this.headers[2].value,
          // totalItems: 0,
        },
      }
    },
    computed: {
      pages() {
        if (this.pagination.rowsPerPage == null ||
          this.pagination.totalItems == null
        ) return 0;

        return Math.ceil(this.pagination.totalItems / this.pagination.rowsPerPage)
      }
    },
    mounted: function () {
      if (this && this.headers && this.headers[2] && this.headers[3]) {
        if (this.tableData.isNowPlayCount) {
          this.pagination.sortBy = this.headers[2].value;
        } else {
          this.pagination.sortBy = this.headers[3].value;
        }
      }
      console.log(this.headers);
      console.log("this.pagination.sortBy:" + this.pagination.sortBy);
      // this.pagination.descending = "desc";
      // console.log("mounted");
      // console.log(tableData.name);
      // console.log(tableData.isNowPlayCount);
    }
  }
  console.log("end RankTable.vue");
</script>

<style scoped>
</style>
