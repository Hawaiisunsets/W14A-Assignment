<template>
    <div>
        <!-- <button @click="getLoudJoke">Get Loud Joke</button> -->
        <!-- <button>{{jokeLoud}}</button> -->
        <p>{{jokeLoud.toUpperCase()}}</p>
    </div>
</template>

<script>
import axios from "axios";
    export default {
        name : "LoudJoke",
        data(){
            return{
                jokeLoud : []
            }
        },
        // method: {
        //     getLoudJoke(){
        //         this.jokeLoud;
        //     }
        // },
        mounted(){
            axios.request({
                url : "https://geek-jokes.sameerkumar.website/api?format=json",
                method : "GET"
            }).then((response)=>{
                console.log(response.data.joke);
                this.jokeLoud = response.data.joke;
            }).catch((error)=>{
                console.log(error);
            });
        }
    }
</script>

<style scoped>

</style>