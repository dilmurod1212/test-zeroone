<template>
  <div class="wrapper">
    <table class="table">
      <thead>
        <tr>
          <th v-for="(h, index) in head" :key="index">
            {{ h.title }}
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(d, index) in data" :key="index">
          <td v-for="(h, idx) in head" :key="idx">
            {{ d[h.key] }}
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup lang="ts">
import { defineProps } from "vue";
interface Props {
  head: object[];

  data: object[];
}
defineProps<Props>();
</script>
<style scoped>
.wrapper {
  padding: 20px;
  border: 1px dashed black;
}
.table {
  border-collapse: collapse;
  width: 100%;
  text-align: left;
  thead {
    background: #ccc;
    th {
      padding: 10px;
    }
  }
  tbody tr {
    td {
      border: 1px solid rgba(0, 0, 0, 0.1);
      border-right: none;
      border-left: none;
      padding: 10px 6px;
      //background: red;
    }
    td:first-child {
      color: deepskyblue;
    }
    td:last-child {
      color: deepskyblue;
    }
  }
}
</style>
