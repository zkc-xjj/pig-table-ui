<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <pig-table msg="Welcome to Your Vue.js App"></pig-table>
  </div>
</template>

<script>
import pigTable from '../src/package/pig-table/index.vue'

export default {
  name: 'App',
  components: {
    pigTable
  }
}
</script>

<style>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
</style>
