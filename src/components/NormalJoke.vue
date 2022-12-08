<template>
    <div>
        <!-- <div v-for="user in jokeNormal" :key="user">
            {{user.joke}}

        </div> -->
        <p>{{jokeNormal}}</p>
    </div>
</template>

<script>
import axios from "axios";
    export default {
        name : "NormalJoke",
        data(){
            return{
                jokeNormal : []
            }
        },
        mounted(){
            axios.request({
                url : "https://geek-jokes.sameerkumar.website/api?format=json",
                method : "GET"
            }).then((response)=>{
                // console.log(response.data.joke);
                this.jokeNormal = response.data.joke;
            }).catch((error)=>{
                console.log(error);
            });
        }
    }
</script>

<style scoped>

</style>