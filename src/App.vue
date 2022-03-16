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

*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

img{
  max-width: 100%;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

</style>
