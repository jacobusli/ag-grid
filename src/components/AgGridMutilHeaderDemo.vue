<template>
  <h1 class="banner">{{ title }}</h1>
  <!-- The AG Grid component -->
  <AgGridVue style="width: 100%; height: 1000px" :columnDefs="colDefs" :rowData="rowData" />
</template>

<style scoped>
.banner {
  background-color: antiquewhite;
}
</style>

<script setup lang="ts" name="AgGridMultiHeaderDemo">
import { ref } from 'vue';
import { AgGridVue } from "ag-grid-vue3"; // Vue Data Grid Component
import { AllCommunityModule, ModuleRegistry } from 'ag-grid-community';
// Register all Community features
ModuleRegistry.registerModules([AllCommunityModule]);

let title = "AgGridMultiHeaderDemo";

const rowData = ref<IRow[]>([
  { FunctionCode: "Tesla", VarNo: "VarNo. Y", SI: 64950, Spec: "36", modelQty: 37 },
  { FunctionCode: "Ford", VarNo: "F-Series", SI: 33850, Spec: "", modelQty: 0 },
  { FunctionCode: "Toyota", VarNo: "Corolla", SI: 29600, Spec: "", modelQty: 0 },
  { FunctionCode: "Mercedes", VarNo: "EQA", SI: 48890, Spec: "", modelQty: 0 },
]);

const colDefs = ref<(ColDef | ColGroupDef)[]>([
  {
    headerName: "",
    headerClass: "header-up-extend",
    children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "IPL/Prot", headerClass: "header-parent", children: [{ field: "FunctionCode" }, { field: "VarNo" }, { field: "SI" },] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "BODY",
    headerClass: "header-up-data",
    children: [{ headerName: "ENGINE", headerClass: "header-up-data", children: [{ headerName: "AXLE", headerClass: "header-up-data", children: [{ headerName: "HANDLE", headerClass: "header-up-data", children: [{ headerName: "GRADE", headerClass: "header-up-data", children: [{ headerName: "TRANS", headerClass: "header-up-data", children: [{ headerName: "YEAR", headerClass: "header-up-data", children: [{ headerName: "INTAKE", headerClass: "header-up-data", children: [{ headerName: "ZONE", headerClass: "header-up-data", children: [{ headerName: "EQUIP", headerClass: "header-up-data", children: [{ field: "Spec", }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "001", field: "modelQty" }] }] }] }] }] }] }] }] }] }],
  },
]);
</script>
