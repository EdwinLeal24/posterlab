<template>
  <div id="app">
    <GChart
      :settings="{packages: ['bar']}"
      :data="chartData"
      :options="chartOptions"
      :create-chart="(el, google) => new google.charts.Bar(el)"
      @ready="onChartReady"
    />
  </div>
</template>

<script>
import { GChart } from 'vue-google-charts'
import keywords from '../data/keywords'

export default {
  name: 'App',
  components: {
    GChart
  },
  props: {
    title: {
      type: String,
      default: 'Title'
    },
    subtitle: {
      type: String,
      default: 'Subtitle'
    },
    keyword: {
      type: Array,
      default: null
    }
  },
  data () {
    return {
      chartsLib: null,
      chartData: keywords.map(el => Array.from(Object.values(el)))
    }
  },
  computed: {
    chartOptions () {
      if (!this.chartsLib) { return null }
      return this.chartsLib.charts.Bar.convertOptions({
        chart: {
          title: this.title,
          subtitle: this.subtitle
        },
        hAxis: { format: 'none' },
        width: 550,
        height: 400,
        colors: ['#3f8eab']
      })
    }
  },
  methods: {
    onChartReady (chart, google) {
      this.chartsLib = google
    }
  }
}
</script>
