<template>
    <div>
        <button @click="getSnake">Snake Joke: {{jokeSnake.replace(/ /g,"_")}}</button>
        <p>{{jokeSnake.replace(/ /g,"_")}}</p>
    </div>
</template>

<script>
import axios from "axios";
    export default {
        name : "SnakeJoke",
        data(){
            return{
                jokeSnake : []
            }
        },
        methods : {
            getSnake(){
                this.jokeSnake = [];
            }
        },
        mounted(){
            axios.request({
                url : "https://geek-jokes.sameerkumar.website/api?format=json",
                method : "GET"
            }).then((response)=>{
                // console.log(response.data.joke);
                this.jokeSnake = response.data.joke;
            }).catch((error)=>{
                console.log(error);
            });
        }
    }
</script>

<style scoped>

</style>