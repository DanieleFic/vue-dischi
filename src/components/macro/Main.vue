<template>
  <div class="ms_main">
    <div class="container">
      <Input
      @cerca="cambioValore"
      />
      <!-- <InputArtisti
      @cercaArtisti="cambioValoreAristi"
      /> -->
        <div v-if="!loading" class="row">
          <ListaDischi
          v-for="(element,index) in filtraGeneri"
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
import Input from "../common/_Input.vue"
/* import InputArtisti from "../common/InputArtist.vue" */

export default {
  name: 'Main',
  components: {
    ListaDischi,
    Loader,
    Input,
    /* InputArtisti */
  },
  data() {
        return {
            apiURL: "https://flynn.boolean.careers/exercises/api/array/music",
            dischiArray: [],
            loading: true,
            valore:"",
            /* valoreArtisti:"" */
        }
    },
    created(){
        this.getAlbum();
        //console.log(this.dischiArray)
    },
    computed: {
        filtraGeneri(){
          if(this.valore == "Null") return this.dischiArray
          
                return this.dischiArray.filter( (album) => {
                console.log('filtra album');
                return album.genre.includes(this.valore) /* || album.author.includes(this.valoreArtisti) */ ;
            });
        }
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
        },
        cambioValore(event){
            this.valore = event;
            console.log(this.valore);  
          }
        },
        /* cambioValoreAristi(e){
            this.valoreArtisti = e;
            console.log(this.valoreArtisti);  
          },  */
        }
        /* valueSelect(){

        } */

    

</script>

<style scoped lang="scss">
@import "../../assets/style/vars.scss";

    .ms_main{
        height: calc(100vh - 45px);
        background-color: $maincolor;

        .container{
          padding: 50px 0px;
          text-align: center;
        }
    }
</style>