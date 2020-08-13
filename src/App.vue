<template>
  <div id="app" class="small-container">
    <API/>
  </div>
</template>

<script>
import API from './components/API.vue'

export default {
  name: 'App',
  components: {
    API
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
