<template>
  <div>
    <Header />
    <div>
      <Title title="KPI Graphs" />
      <div class="container pt-10">
        <Graphs :data="dataKeywords" title="Most used keyword" subtitle="Count of de most used keywords" color="#3f8eab" />
        <Graphs
          :data="dataTopics"
          bar="horizontal"
          title="Most used topics"
          subtitle="Count of de most used topics"
          color="#1D2368"
          :width="700"
        />
      </div>
    </div>
  </div>
</template>

<script>
import keywords from '../data/keywords'
import topics from '../data/topics'
import Graphs from '../components/Graphs'
import Header from '~/components/Header.vue'

export default {
  components: {
    Header,
    Graphs
  },
  data () {
    return {
      dataKeywords: [],
      dataTopics: []
    }
  },
  created () {
    this.dataKeywords = keywords
    this.dataTopics = topics
  }
}

</script>

<style>
.container {
  margin: 0 auto;
  height: 500px;
  display: flex;
  justify-content: space-between;
  text-align: center;
}
</style>
