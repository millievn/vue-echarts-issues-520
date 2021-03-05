<template>
  <div id="app">
    <div class="bar">
      <v-chart ref="bar" :option="barOptions" autoresize />
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import { use } from 'echarts/core'
import { CanvasRenderer } from 'echarts/renderers'
import { PieChart, BarChart } from 'echarts/charts'
import { TitleComponent, TooltipComponent, LegendComponent, DatasetComponent, GridComponent } from 'echarts/components'
import { default as VChart, THEME_KEY } from 'vue-echarts'

use([
  CanvasRenderer,
  PieChart,
  BarChart,
  TitleComponent,
  TooltipComponent,
  LegendComponent,
  DatasetComponent,
  GridComponent,
])

export default Vue.extend({
  name: 'App',
  components: {
    VChart,
  },
  provide: {
    [THEME_KEY]: 'light',
  },
  data() {
    return {
      barOptions: {
        legend: {},
        tooltip: {},
        dataset: {
          source: [
            ['product', 'name', 'price'],
            ['test', 'name', 1],
          ],
        },
        xAxis: { type: 'category' },
        yAxis: {},
        series: [{ type: 'bar' }, { type: 'bar' }],
      },
    }
  },
})
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.bar {
  height: 500px;
}
</style>
