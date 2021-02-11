<template>
  <div class="about">
    <img alt="Vue logo" src="../assets/logo.png">
    <Titulo texto="Bienvenidos a About" />
  </div>
</template>
<script>
// @ is an alias to /src
import Titulo from '../components/Titulo'

export default {
  name: 'About',
  components: {
    Titulo
  }
}
</script>