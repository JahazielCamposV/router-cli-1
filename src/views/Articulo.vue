<template>
  <Titulo texto="Ruta con parametros" />
  <h2>Parámetro: {{ $route.params.id }}</h2>
  <h3>title {{ articulo.title }} </h3>
  <h3>{{articulo.id}} -- {{ articulo.body }} </h3>
</template>

<script>
import Titulo from '../components/Titulo.vue'
export default {
    name: 'Articulo',
    components: {
        Titulo
    },
    data(){
        return{
            articulo: {}
        }
    },
    methods:{
        async consumirArticulo(){
            try {
                const data = await fetch(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`)
                const obj = await data.json()
                this.articulo = obj
            } catch (error) {
                console.log(error)
            }
        }
    },
    created(){
        this.consumirArticulo()
    }

}
</script>

<style>

</style>