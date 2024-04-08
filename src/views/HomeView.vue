<template>
  <div class="list">
    <div>
      <TreeCollapse v-for="item in lists" :key="item.id" v-bind="{ item }" />
    </div>
    <div>
      <Table :data="tableData" :head="tableHead"> </Table>
    </div>
  </div>
</template>

<script setup>
import TreeCollapse from "@/components/TreeCollapse.vue";
import { lists, tableData, tableHead } from "@/data/index.js";
import Table from "@/components/Table.vue";
</script>

<style scoped>
.list {
  padding: 40px;
  display: grid;
  grid-template-columns: 20% 80%;
}
</style>
