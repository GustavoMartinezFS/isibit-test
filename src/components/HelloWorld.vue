<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h3><router-link to="/weather">Weather App</router-link></h3>
 <p>Se diseño una spa en vue la cual, consulta
una API del clima,<br> donde el traveler pueda ver las diferencias del clima <br> entre su cuidad actual y la ciudad a la cual desea viajar.</p>
    Para ello el traveler deberá especificar:
    <ul>
      <li>● Ciudad de origen</li>
      <li>● Ciudad de destino</li>
    </ul>
    <h3><router-link to="/OCR">OCR App</router-link></h3>
    <p>Se realizo la implementación de un proveedor de OCR, en el cual <br> en un formulario le mandamos la imagen del recibo a analizar <br> y mediante su API, obtenemos el resultado y lo mostramos al usuario.</p>
    
 
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: rgb(31,54,255);
}
</style>
