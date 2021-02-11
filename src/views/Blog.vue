<template>
  <div class="blog">
    <img alt="Vue logo" src="../assets/logo.png">
    <Titulo texto="Bienvenidos a Blog" />
    <!-- <button @click="consumirApi">Consumir API</button> -->
    <div v-for="item in arrayBlog" :key="item.id">
        <router-link :to="`/blog/${item.id}`">
            {{item.title}}
        </router-link>
    </div>
  </div>
</template>

<script>
import Titulo from '../components/Titulo'
export default {
    name: 'About',
    components: {
        Titulo
    },
    data() {
        return {
            arrayBlog: []
        }
    },
    methods: {
        async consumirApi(){
            try {
                const data = await fetch('https://jsonplaceholder.typicode.com/posts')
                // const data = await fetch('https://api.sat.ws/rfc/validate/AIA151026EA4', {
                    // headers:{
                    //     'Access-Control-Allow-Origin':'*',
                    //     'Content-Type': 'application/json;charset=utf-8',
                    //     'X-API-Key':'d533d68e76a4ba82d1fd78640317ed63',
                    //     credentials: "include"
                    // }
                // })
                const array = await data.json()
                console.log(array)
                this.arrayBlog = array
            } catch (error) {
                console.log(error)
            }
        }
    },
    created(){
        this.consumirApi()
    }
}
</script>

<style>

</style>