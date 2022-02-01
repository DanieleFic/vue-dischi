<template>
    <div class="box">
    <select v-model="filtra" @change="$emit('cerca', filtra)">
        <!-- <option v-for="(elemento, i) in artistArray" :key="i" :value="elemento.genre">{{ elemento.genre }}</option> -->
        <option value="Null">Tutti</option>
        <option value="Rock">Rock</option>
        <option value="Jazz">Jazz</option>
        <option value="Pop">Pop</option>
        <option value="Metal">Metal</option> 
    </select>
</div>
</template>

<script scoped>

export default {
    name:"Input",
    data(){
        return{
            filtra:"",
        }
    },       
}
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