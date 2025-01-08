<template>
  <h1 class="banner">{{ title }}</h1>
  <!-- The AG Grid component -->
  <ag-grid-vue style="width: 100%; height: 500px" :columnDefs="colDefs" :rowData="rowData"
    :defaultColDef="defaultColDef">
  </ag-grid-vue>
</template>

<script setup lang="ts" name="AgGridMultiHeaderDemo">
import { ref } from 'vue';
import { AgGridVue } from "ag-grid-vue3"; // Vue Data Grid Component
import { AllCommunityModule, ModuleRegistry } from 'ag-grid-community';
// Register all Community features
ModuleRegistry.registerModules([AllCommunityModule]);

let title = "AgGridMultiHeaderDemo";

const rowData = ref<IRow[]>([
  { make: "Tesla", model: "Model Y", price: 64950, electric: true },
  { make: "Ford", model: "F-Series", price: 33850, electric: false },
  { make: "Toyota", model: "Corolla", price: 29600, electric: false },
  { make: "Mercedes", model: "EQA", price: 48890, electric: true },
  { make: "Fiat", model: "500", price: 15774, electric: false },
  { make: "Nissan", model: "Juke", price: 20675, electric: false },
]);

const colDefs = ref<ColDef<IRow>[]>([
  { field: "make" },
  { field: "model" },
  { field: "price" },
  { field: "electric" },
]);

const defaultColDef = {
  flex: 1,
};
</script>

<style scoped>
.banner {
  background-color: antiquewhite;
}
</style>
