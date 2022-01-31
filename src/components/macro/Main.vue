<template>
  <div class="ms_main">
    <div class="container">
        <div class="row">
          <ListaDischi/>
        </div>
    </div>
  </div>
  
</template>

<script>
import ListaDischi from "../common/ListaDischi.vue" 
export default {
  name: 'Main',
components: {
    ListaDischi,
  
  }
  }
</script>

<style scoped lang="scss">
@import "../../assets/style/vars.scss";

    .ms_main{
        height: calc(100vh - 45px);
        background-color: $maincolor;
    }
</style>