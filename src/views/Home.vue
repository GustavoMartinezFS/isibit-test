<template>
  <div class="home">
    <img alt="isibit logo" width='300px' src="https://res-2.cloudinary.com/crunchbase-production/image/upload/c_lpad,f_auto,q_auto:eco/ldq52soza1tv6bu43604">
    <HelloWorld msg="Prueba Js Developer - Test"/>
  </div>
</template>

<script>
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld
  }
}
</script>
