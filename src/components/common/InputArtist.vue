<template>
    <div class="box">
        <select v-model="filtraArtist" @change="$emit('cercaArtisti', filtraArtist)" >
            <option  v-for="(element, index) in artistArray" :key="index" :value="element.author">{{ element.author }}</option>
        </select>
    </div>
</template>

<script>
import axios from "axios";
export default {
    name:"InputArtisti",
    data(){
        return{
            filtraArtist:"",
            artistArray:[],
            apiURL: "https://flynn.boolean.careers/exercises/api/array/music",
        } 
    },
    created(){
        this.getArtist();
        //console.log(this.dischiArray)
    },
    methods: {
        getArtist(){
            axios
                .get(this.apiURL)
                .then( (risposta) => {
                    // handle success
                    this.artistArray = risposta.data.response;
                    this.loading = false;
                })
                .catch(function (error) {
                    // handle error
                    console.log(error);
                });
        },
}}
</script>

<style scoped lang="scss">
    @import "../../assets/style/vars.scss";


    select {
    background-color: $headercolor;
    color: white;
    padding: 12px;
    width: 250px;
    border: none;
    font-size: 20px;
    box-shadow: 0 5px 25px rgba(0, 0, 0, 0.2);
    outline: none;

}

.box select option {
    padding: 30px;
}
</style>