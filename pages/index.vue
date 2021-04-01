<template>
  <div>
    <Header />
    <div>
      <Title title="KPI Graphs" />
      <div class="container pt-10">
        <Graphs title="Most used keyword" subtitle="Count of de most used keywords" />
        <Graphs />
      </div>
    </div>
  </div>
</template>

<script>
import Header from '~/components/Header.vue'
export default {
  components: {
    Header
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
