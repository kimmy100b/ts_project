<template>
    <div>
        <div class="Main-d-tabs">
            <el-tabs v-model="activeTab" type="border-card" @tab-click="setTabName">
                <el-tab-pane
                    v-for="tab in tabs"
                    :key="tab.key"
                    :label="tab.name"
                    :name="tab.comp"
                >
                </el-tab-pane>
                <component class="Main-d-comps" :is="activeTab" v-bind:tabTitle="tabTitle"></component>
            </el-tabs>
        </div>
    </div>
</template>

<script lang="ts">
import agGrid from './MainAgGrid.vue'
import collapse from './MainCollapse.vue'

import { Tabs } from 'vue/types/vue'

declare module 'vue/types/vue' {
  interface Tabs {
    key: number;
    name: string;
    comp: string;
  }
}

export default {
  data (): { activeTabName: string; activeTab: string; tabTitle: string; tabs: Tabs[] } {
    return {
      activeTabName: '' as string,
      activeTab: '' as string,
      tabTitle: '' as string,
      tabs: [{
        key: 1,
        name: 'Ag-Grid TypeScript',
        comp: 'ag-grid-pane' // agGridTs
      },
      {
        key: 2,
        name: 'Collapse',
        comp: 'collapse-pane'
      }
      ] as Tabs[]
    }
  },
  created (): void {
    this.activeTab = this.tabs[0].comp
    this.activeTabName = this.tabs[0].name
    this.tabTitle = this.setTitle()
  },
  methods: {
    setTabName (tab: { label: string }) : void {
      this.activeTabName = tab.label
      this.tabTitle = this.setTitle()
      console.log(this.tabTitle)
    },
    setTitle () : string {
      return 'This is ' + this.activeTabName + ' Page'
    }
  },
  components: {
    'ag-grid-pane': agGrid,
    'collapse-pane': collapse
  }
}
</script>

<style>
.Main-d-tabs {
  margin: 50px;
}

.Main-d-comps {
  height: 500px;
  margin: 50px;
}
</style>
