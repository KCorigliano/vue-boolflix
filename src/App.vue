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
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

</style>
