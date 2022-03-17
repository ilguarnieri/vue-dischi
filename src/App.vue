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



/* Descrizione:
Generale la lista dei generi dall’array di album per stampare dinamicamente le option della select
(quindi dove capire come far arrivare questi dati alla select, in base a come strutturate i vostri componenti)

Aggiungere un ulteriore select che filtra gli album per artista,
(anche per questa option generate le option degli artisti dinamicamente).
Buon lavoro e buon week end */

</style>
