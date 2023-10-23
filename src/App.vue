<template>
  <div id="app">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <!-- <Demo2 /> -->
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
// import Demo2 from '@/components/demo2'

export default {
  name: 'App',
  components: {
    HelloWorld,
    // Demo2
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
