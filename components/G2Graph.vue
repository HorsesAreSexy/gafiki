<template>
  <div :id="`graph${graphOrder}`" />
</template>

<script>
import { Chart } from '@antv/g2'
export default {
  name: 'G2Graph',
  props: {
    graphData: {
      type: Array,
      default: () => []
    },
    graphType: {
      type: String,
      default: ''
    },
    graphOrder: {
      type: Number,
      default: 0
    },
    settingDots: {
      type: Number,
      default: 0
    }
  },
  data () {
    return {
      chart: null
    }
  },
  watch: {
    settingDots (value) {
      this.chart.tooltip(!value)
    },
    graphData (value) {
      this.chart.changeData(value)
    }
  },
  mounted () {
    const chart = new Chart({
      container: `graph${this.graphOrder}`,
      autoFit: true
    })
    this.chart = chart
    chart.data(this.graphData)
    const geom = chart[this.graphType === 'column' ? 'interval' : 'line']().position('group*value')
    if (this.graphType === 'step') {
      geom.shape('hv')
    }
    chart.render()
  }
}
</script>
