<template>
  <div class="ms_main">
    <div class="container">
        <div v-if="!loading" class="row">
          <ListaDischi
          v-for="(element,index) in dischiArray"
          :key="index"
          :info="element"
          class=" col-12 col-sm-6 col-lg-2"/>
        </div>
        <Loader v-else />
    </div>
  </div>
  
</template>

<script>
import axios from "axios";
import ListaDischi from "../common/ListaDischi.vue"
import Loader from "../common/Loading.vue"

export default {
  name: 'Main',
  components: {
    ListaDischi,
    Loader
  },
  data() {
        return {
            apiURL: "https://flynn.boolean.careers/exercises/api/array/music",
            dischiArray: [],
            loading: true
        }
    },
    created(){
        this.getAlbum();
        //console.log(this.dischiArray)
    },
    methods: {
        getAlbum(){
            axios
                .get(this.apiURL)
                .then( (risposta) => {
                    // handle success
                    this.dischiArray = risposta.data.response;
                    this.loading = false;
                    
                    
                })
                .catch(function (error) {
                    // handle error
                    console.log(error);
                });
        }
    }
}
</script>

<style scoped lang="scss">
@import "../../assets/style/vars.scss";

    .ms_main{
        height: calc(100vh - 45px);
        background-color: $maincolor;

        .container{
          padding: 50px 0px;
        }
    }
</style>