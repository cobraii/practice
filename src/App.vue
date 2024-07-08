<template>
  <div class="container" id="app">
    <DataTable />
    <DataTableTwo />
  </div>
</template>

<script>
import DataTable from './components/DataTable.vue';
import DataTableTwo from './components/DataTableTwo.vue';
export default {
  components: {
    DataTable,
    DataTableTwo
  },
};
</script>

<style>

</style> 