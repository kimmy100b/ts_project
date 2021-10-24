<template>
    <div>
        <div class="MainAgGrid-d-title">{{ tabTitle }}</div>
        <ag-grid-vue
            class="ag-theme-alpine MainAgGrid-ag-grid"
            :columnDefs="columnDefs"
            :rowData="rowData"
        >
        </ag-grid-vue>
    </div>
</template>

<script lang="ts">
import { AgGridVue } from 'ag-grid-vue'
import 'ag-grid-community/dist/styles/ag-grid.css'
import 'ag-grid-community/dist/styles/ag-theme-alpine.css'

export default {
  props: {
    tabTitle: String
  },
  data (): {
    columnDefs: { headerName: string; field: string, sortable?: boolean, flex?: 1, width?: number }[];
    rowData: { make: string; model: string; price: number }[]
    } {
    return {
      columnDefs: [
        { headerName: 'Make', field: 'make', sortable: true, flex: 1 },
        { headerName: 'Model', field: 'model', width: 400 },
        { headerName: 'Price', field: 'price', width: 300 }
      ],
      rowData: [
        { make: 'Toyota', model: 'Celica', price: 35000 },
        { make: 'Ford', model: 'Mondeo', price: 32000 },
        { make: 'Porsche', model: 'Boxter', price: 72000 }
      ]
    }
  },
  components: {
    'ag-grid-vue': AgGridVue
  }
}
</script>

<style>
.MainAgGrid-ag-grid {
  width: 100%;
  height: calc( 100% - 50px )
}

.MainAgGrid-d-title {
  margin-bottom: 20px;
  font-size: 25px;
  font-weight: bold;
}
</style>
