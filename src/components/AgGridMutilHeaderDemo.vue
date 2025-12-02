<template>
  <h1 class="banner">{{ title }}</h1>
  <!-- The AG Grid component -->
  <AgGridVue style="width: 100%; height: 1000px" :columnDefs="colDefs" :rowData="rowData" :defaultColDef="defaultColDef"
    :tooltipShowDelay="200" />
</template>

<style scoped>
.banner {
  background-color: antiquewhite;
}
</style>

<style>
/* Tooltip with yellow background */
.ag-tooltip {
  background-color: yellow !important;
  color: black !important;
  padding: 8px 12px !important;
  border: 1px solid #ccc !important;
  border-radius: 4px !important;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15) !important;
}
</style>

<script setup lang="ts" name="AgGridMultiHeaderDemo">
import { ref } from 'vue';
import { AgGridVue } from "ag-grid-vue3"; // Vue Data Grid Component
import { AllCommunityModule, ModuleRegistry, type ColDef, type ColGroupDef } from 'ag-grid-community';
// Register all Community features
ModuleRegistry.registerModules([AllCommunityModule]);

let title = "AgGridMultiHeaderDemo";

// Default column definition with tooltip for all cells
const defaultColDef = ref<ColDef>({
  tooltipValueGetter: (params: any) => {
    // Check if current column has corresponding Err property
    if (params.colDef.field) {
      const errField = params.colDef.field + 'Err';
      const errValue = params.data[errField];
      if (errValue && errValue.length > 0) {
        return 'The value has already exists!!';
      }
    }
    return '';
  },
});

const rowData = ref<any[]>([]);
for (let i = 1; i <= 8000; i++) {
  var data = { "no": i, "designNoteNo": "AL4154*00133", "FunctionCode": "G50010---", "varNo": "024", "designerNote": "EMTISA CAR2ND M9T EUR06 LHD 4WD REPAIR", "na": "N", "si": "010", "su": "O", "level": "1", "r": "R", "partNoBefore": "501009116C", "partNo": "501009116D", "partRev": "--B", "partName": "REINF-EXT SIDE MBR,LWR LH", "pc": "01", "generic": "F18051/NB", "g": "-", "s": "-", "Spec": "-", "modelQty1": "0", "modelQty2": "1", "modelQty3": "1", "modelQty4": "1", "modelQty5": "0", "modelQty6": "0", "modelQty7": "1", "modelQty8": "0", "modelQty9": "0", "modelQty10": "1", "modelQty11": "0", "modelQty12": "0", "modelQty13": "0", "modelQty14": "0", "modelQty15": "0", "modelQty16": "0", "modelQty17": "0", "modelQty18": "0", "modelQty19": "0", "modelQty20": "0", "modelQty21": "0", "modelQty22": "0", "modelQty23": "0", "modelQty24": "0", "modelQty25": "0", "modelQty26": "0", "modelQty27": "0", "modelQty28": "0", "modelQty29": "0", "modelQty30": "0", "modelQty31": "0", "modelQty32": "0", "modelQty33": "0", "modelQty34": "0", "modelQty35": "0", "modelQty36": "0", "modelQty37": "0", "modelQty38": "0", "modelQty39": "0", "modelQty40": "0", "modelQty41": "0", "modelQty42": "0", "modelQty43": "0", "modelQty44": "0", "modelQty45": "0", "modelQty46": "0", "modelQty47": "0", "modelQty48": "0", "modelQty49": "0", "modelQty50": "0", "modelQty51": "0", "modelQty52": "0", "modelQty53": "0", "modelQty54": "0", "modelQty55": "0", "modelQty56": "0", "modelQty57": "0", "modelQty58": "0", "modelQty59": "0", "modelQty60": "0", "modelQty61": "0", "modelQty62": "0", "modelQty63": "0", "modelQty64": "0", "modelQty65": "0", "modelQty66": "0", "modelQty67": "0", "modelQty68": "0", "modelQty69": "0", "modelQty70": "0", "modelQty71": "0", "modelQty72": "0", "modelQty73": "0", "modelQty74": "0", "modelQty75": "0", "modelQty76": "0", "modelQty77": "0", "modelQty78": "0", "modelQty79": "0", "modelQty80": "0", "modelQty81": "0", "modelQty82": "0", "modelQty83": "0", "modelQty84": "0", "modelQty85": "0", "modelQty86": "0", "modelQty87": "0", "modelQty88": "0", "modelQty89": "0", "modelQty90": "0", "modelQty91": "0", "modelQty92": "0", "modelQty93": "0", "modelQty94": "0", "modelQty95": "0", "modelQty96": "0", "modelQty97": "0", "modelQty98": "0", "modelQty99": "0", "modelQty100": "0", "modelQty101": "0", "modelQty102": "0", "modelQty103": "0", "modelQty104": "0", "modelQty105": "0", "modelQty106": "0", "modelQty107": "0", "modelQty108": "0", "modelQty109": "0", "weight": "2964", "importantPartsSymbol": "0", "note": "5LINK W/ENCAP", "dwg": "501794JK3A", "dwgRev": "-02", "meterial": "HE 450M T3.0", "assessmentLevel": "22", "cumpm1": "Mark 1", "cumpm2": "Mark 2", "originPartNumber": "501009116C", "category": "Category A", "opnl": "Localization", "supplier": "A217", "supplierFlag": "NONEED", "lccp": "Not sensitive", "lccs": "Not sensitive", "originNumberCompany": "A217", "specTenderNumber": "S0002100", "conf": "Renault", "nmpm": "Mark 3", "standardPart": "501009116C", "nesNumber": "501009116C", "mfgMethod": "G50010---", "processVolume": "2045Gb", "supplierTestStatus": "Approved", "dsmp": "501009116C", "dsrl": "005", "ncCode": "Nissan_Code", "mutiUsagePartNo": "501009116C", };

  // Add Err properties for all fields except 'no'
  for (const key in data) {
    if (key !== 'no') {
      (data as any)[key + 'Err'] = [{ id: "NB038" }];
    }
  }

  rowData.value.push(data);
}


const colDefs = ref<(ColDef | ColGroupDef)[]>([
  {
    headerName: "",
    headerClass: "header-up-extend",
    children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "No", field: "no" }, { headerName: "D/Note No.", field: "designNoteNo" }, { headerName: "Var No.", field: "varNo" }, { headerName: "Function Code", field: "FunctionCode" }, { headerName: "Desiner Note", field: "designerNote" }, { headerName: "N/A", field: "na" }, { headerName: "SI", field: "si" }, { headerName: "S U", field: "su" }, { headerName: "Level", field: "level" }, { headerName: "R", field: "r" }, { headerName: "Part Number(Before)", field: "partNoBefore" }, { headerName: "Part Number(After)", field: "partNo" }, { headerName: "Part Rev", field: "partRev" }, { headerName: "Part Name", field: "partName" }, { headerName: "P C", field: "pc" }, { headerName: "Generic#", field: "generic" }, { headerName: "G", field: "g" }, { headerName: "S", field: "s" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "BODY",
    headerClass: "header-up-data",
    children: [{ headerName: "ENGINE", headerClass: "header-up-data", children: [{ headerName: "AXLE", headerClass: "header-up-data", children: [{ headerName: "HANDLE", headerClass: "header-up-data", children: [{ headerName: "GRADE", headerClass: "header-up-data", children: [{ headerName: "TRANS", headerClass: "header-up-data", children: [{ headerName: "YEAR", headerClass: "header-up-data", children: [{ headerName: "INTAKE", headerClass: "header-up-data", children: [{ headerName: "ZONE", headerClass: "header-up-data", children: [{ headerName: "EQUIP", headerClass: "header-up-data", children: [{ field: "Spec", }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "001", field: "modelQty1" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "002", field: "modelQty2" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "003", field: "modelQty3" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "004", field: "modelQty4" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "005", field: "modelQty5" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "006", field: "modelQty6" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "007", field: "modelQty7" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "008", field: "modelQty8" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "009", field: "modelQty9" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "010", field: "modelQty10" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "011", field: "modelQty11" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "012", field: "modelQty12" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "013", field: "modelQty13" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "014", field: "modelQty14" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "015", field: "modelQty15" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "016", field: "modelQty16" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "017", field: "modelQty17" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "018", field: "modelQty18" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "019", field: "modelQty19" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "020", field: "modelQty20" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "021", field: "modelQty21" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "022", field: "modelQty22" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "023", field: "modelQty23" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "024", field: "modelQty24" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "025", field: "modelQty25" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "026", field: "modelQty26" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "027", field: "modelQty27" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "028", field: "modelQty28" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "029", field: "modelQty29" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "030", field: "modelQty30" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "031", field: "modelQty31" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "032", field: "modelQty32" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "033", field: "modelQty33" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "034", field: "modelQty34" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "035", field: "modelQty35" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "036", field: "modelQty36" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "037", field: "modelQty37" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "038", field: "modelQty38" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "039", field: "modelQty39" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "040", field: "modelQty40" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "041", field: "modelQty41" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "042", field: "modelQty42" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "043", field: "modelQty43" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "044", field: "modelQty44" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "045", field: "modelQty45" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "046", field: "modelQty46" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "047", field: "modelQty47" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "048", field: "modelQty48" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "049", field: "modelQty49" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "050", field: "modelQty50" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "051", field: "modelQty51" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "052", field: "modelQty52" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "053", field: "modelQty53" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "054", field: "modelQty54" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "055", field: "modelQty55" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "056", field: "modelQty56" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "057", field: "modelQty57" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "058", field: "modelQty58" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "059", field: "modelQty59" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "060", field: "modelQty60" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "061", field: "modelQty61" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "062", field: "modelQty62" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "063", field: "modelQty63" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "064", field: "modelQty64" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "065", field: "modelQty65" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "066", field: "modelQty66" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "067", field: "modelQty67" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "068", field: "modelQty68" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "069", field: "modelQty69" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "070", field: "modelQty70" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "071", field: "modelQty71" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "072", field: "modelQty72" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "073", field: "modelQty73" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "074", field: "modelQty74" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "075", field: "modelQty75" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "076", field: "modelQty76" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "077", field: "modelQty77" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "078", field: "modelQty78" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "079", field: "modelQty79" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "080", field: "modelQty80" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "081", field: "modelQty81" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "082", field: "modelQty82" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "083", field: "modelQty83" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "084", field: "modelQty84" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "085", field: "modelQty85" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "086", field: "modelQty86" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "087", field: "modelQty87" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "088", field: "modelQty88" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "089", field: "modelQty89" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "090", field: "modelQty90" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "091", field: "modelQty91" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "092", field: "modelQty92" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "093", field: "modelQty93" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "094", field: "modelQty94" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "095", field: "modelQty95" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "096", field: "modelQty96" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "097", field: "modelQty97" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "098", field: "modelQty98" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "099", field: "modelQty99" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "100", field: "modelQty100" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "101", field: "modelQty101" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "102", field: "modelQty102" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "103", field: "modelQty103" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "104", field: "modelQty104" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "105", field: "modelQty105" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "106", field: "modelQty106" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "107", field: "modelQty107" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "108", field: "modelQty108" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "F",
    headerClass: "header-up-data",
    children: [{ headerName: "CR", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "R", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "9", headerClass: "header-up-data", children: [{ headerName: "-", headerClass: "header-up-data", children: [{ headerName: "H", headerClass: "header-up-data", children: [{ headerName: "J", headerClass: "header-up-data", children: [{ headerName: "A", headerClass: "header-up-data", children: [{ headerName: "109", field: "modelQty109" }] }] }] }] }] }] }] }] }] }],
  }, {
    headerName: "",
    headerClass: "header-up-extend",
    children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "", headerClass: "header-up-extend", children: [{ headerName: "Estimated Weight(g)", field: "weight" }, { headerName: "Important Partss Symbol", field: "importantPartsSymbol" }, { headerName: "Note", field: "note" }, { headerName: "Dwg#/Shape#", field: "dwg" }, { headerName: "Rev", field: "dwgRev" }, { headerName: "Material", field: "meterial" }, { headerName: "Assessment Level", field: "assessmentLevel" }, { headerName: "Common Usage Management Part Mark1", field: "cumpm1" }, { headerName: "Common Usage Management Part Mark2", field: "cumpm2" }, { headerName: "Original Part Number", field: "originPartNumber" }, { headerName: "CommonCategory", field: "category" }, { headerName: "Original Part Number For Localization", field: "opnl" }, { headerName: "Supplier(Part Drawing Distribution)", field: "supplier" }, { headerName: "List Control Classification(Part)", field: "lccp" }, { headerName: "Supplier(Part Drawing Distribution) - Flag", field: "supplierFlag" }, { headerName: "List Control Classification(Shape)", field: "lccs" }, { headerName: "Original Part Number Company", field: "originNumberCompany" }, { headerName: "Spec Tender Number", field: "specTenderNumber" }, { headerName: "Conf(Confidential to Renault)", field: "conf" }, { headerName: "Notification Management Part Mark", field: "nmpm" }, { headerName: "Standard Part", field: "standardPart" }, { headerName: "NES Number", field: "nesNumber" }, { headerName: "MFG Method", field: "mfgMethod" }, { headerName: "Process Volume", field: "processVolume" }, { headerName: "Supplier Test Status", field: "supplierTestStatus" }, { headerName: "Design Specification Management Part Number", field: "dsmp" }, { headerName: "Design Specification Revision Level", field: "dsrl" }, { headerName: "Nissan / Certification Code", field: "ncCode" }, { headerName: "Multiusage Part Code", field: "mutiUsagePartNo" }] }] }] }] }] }] }] }] }] }],
  },
]);
</script>
