<template>
  <div id="app">
    <ApiYoutube />
  </div>
</template>

<script>
import ApiYoutube from '../components/apiYoutube.vue'

export default {
  components: {
    ApiYoutube
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
