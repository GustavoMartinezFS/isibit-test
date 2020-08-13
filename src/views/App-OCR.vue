<template>
  <div id='app'>
    <h1>No pierdas mas tu factura</h1>
    <p>Para no cargar tantos papeles, sube aqui tu factura <br> y quedara guardada para lo que necesites!</p>
    <Ocr />
  </div>
</template>

<script>
import Ocr from '@/components/Ocr.vue'

export default {
  name: 'AppOCR',
  components:{
    Ocr
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
