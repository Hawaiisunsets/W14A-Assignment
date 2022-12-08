<template>
  <div id="app">
    <button @click="makeApi">Joke Button:{{jokeApp}}</button>
    <LoudJoke/>
    <NormalJoke/>
    <SnakeJoke/>
  </div>
</template>

<script>
import LoudJoke from "@/components/LoudJoke.vue";
import NormalJoke from "@/components/NormalJoke.vue";
import SnakeJoke from "@/components/SnakeJoke.vue";
import axios from "axios";



export default {
  name: 'App',
  components: {
    LoudJoke,
    NormalJoke,
    SnakeJoke
  },
  data(){
    return{
      jokeApp : []
    }
  },
  methods: {
    makeApi(){
      axios.request({
                url : "https://geek-jokes.sameerkumar.website/api?format=json",
                method : "GET"
            }).then((response)=>{
                // console.log(response.data.joke);
                this.jokeApp = response.data.joke;
            }).catch((error)=>{
                console.log(error);
            });
    }
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
