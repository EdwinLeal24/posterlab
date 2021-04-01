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
    }
  },
  data () {
    return {
      chartsLib: null,
      chartData: [
        ['keyword', 'count'],
        ['investigation', 1000],
        ['share', 1170],
        ['technology', 1100],
        ['office', 350]
      ]
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
