<template>
  <div id="app">
    <demo></demo>
    <demo2></demo2>
  </div>
</template>

<script>
import Demo from './components/Demo.vue'
import Demo2 from './components/Demo2.vue'

export default {
  name: 'App',
  components: {
    Demo,
    Demo2
  }
}
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
</style>
