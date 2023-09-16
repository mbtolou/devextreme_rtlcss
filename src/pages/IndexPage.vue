<template>
  <q-page class="full-width full-height">
    <div>
      <DxDataGrid
        id="gridContainer"
        :data-source="employees"
        key-expr="ID"
        :rtl-enabled="true"
        :allow-column-reordering="true"
        :allow-column-resizing="true"
        :column-auto-width="false"
        :show-borders="true"
        :scrolling="{ useNative: true }"
      >
        <DxColumnChooser :enabled="true" />
        <DxColumnFixing :enabled="true" />
        <DxColumn
          :width="230"
          :fixed="true"
          :calculate-cell-value="calculateCellValue"
          caption="Employee (1)"
        />
        <DxColumn data-field="first column" data-type="date" />
        <DxColumn data-field="second column" data-type="date" />
        <DxColumn data-field="Position" alignment="right" />
        <DxColumn data-field="Address" />
        <DxColumn data-field="City" />
        <DxColumn data-field="State" />
        <DxColumn :visible="false" data-field="Zipcode" />
        <DxColumn data-field="HomePhone" />
        <DxColumn data-field="MobilePhone" />
        <DxColumn data-field="Skype" />
        <DxColumn data-field="last column" />
        <DxPaging :page-size="5" />
      </DxDataGrid>
    </div>
  </q-page>
</template>

<script>
import {
  DxDataGrid,
  DxColumn,
  DxColumnChooser,
  DxColumnFixing,
  DxPaging,
} from "devextreme-vue/data-grid";

import service from "./data.js";

export default {
  components: {
    DxDataGrid,
    DxPaging,
    DxColumn,
    DxColumnChooser,
    DxColumnFixing,
  },
  data() {
    return {
      employees: service.getEmployees(),
    };
  },
  methods: {
    calculateCellValue(data) {
      return [data.Title, data.FirstName, data.LastName].join(" ");
    },
  },
};
</script>
<style scoped>
#gridContainer {
  height: 440px;
}
</style>
