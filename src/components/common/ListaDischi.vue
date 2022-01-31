<template>
  <div class="ms_boxdisco">
      <img :src="info.poster" alt="">
      <h4>{{info.title}}</h4>
      <p>{{info.author}}</p>
      <p>{{info.year}}</p>
  </div>
</template>

<script>
export default {
  name: 'ListaDischi',
  props: {
        info: Object
    }
}
</script>

<style  lang="scss" scoped>
@import "../../assets/style/vars.scss";



.ms_boxdisco{
  color: white;
  text-align: center;
  height: 350px;
  background-color: $headercolor;
  margin: 20px 20px;

  img{
    width: 180px;
    padding: 10px 0px;
  }

  h4{
    padding-bottom: 15px;
  }

  p{
    margin: 0;
    color: $text-color;
    font-size: 13px;
  }

}
</style>