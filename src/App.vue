<template>
  <div id="app">

    <SpHeader />
    <SpMain />
    
  </div>
</template>

<script>
import SpHeader from './components/SpHeader.vue'
import SpMain from './components/SpMain.vue'

export default {
  name: 'App',
  components: {
    SpHeader,
    SpMain
  }
}
</script>

<style lang="scss">
@import './assets/scss/common.scss';

#app {
  font-family: Montserrat, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;  
}

</style>