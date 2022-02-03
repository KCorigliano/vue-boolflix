<template>
  <div id="app">
    <header-box />
    <main-container />
  </div>
</template>

<script>
import MainContainer from './components/MainContainer.vue'
import HeaderBox from './components/HeaderBox.vue'

export default {
  name: 'App',
  components: {
    MainContainer,
    HeaderBox,
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
