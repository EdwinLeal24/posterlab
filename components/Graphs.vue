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
    },
    data: {
      type: Array,
      default: null
    },
    color: {
      type: String,
      default: '#42E3DE'
    },
    bar: {
      type: String,
      default: ''
    },
    width: {
      type: Number,
      default: 550
    }
  },
  data () {
    return {
      chartsLib: null,
      chartData: !this.data ? null : this.data.map(el => Array.from(Object.values(el)))
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
        bars: this.bar,
        hAxis: { format: 'decimal' },
        width: this.width,
        height: 400,
        colors: [this.color]
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
