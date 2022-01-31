<template>
  <div class="ms_header">
    <div class="container-fluid">
        <div class="ms_icon">
            <img src="../../assets/img/Spotify_icon.png" alt="">
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Header',
  
}
</script>

<style scoped lang="scss">
@import "../../assets/style/vars.scss";

    .ms_header{
        background-color: $headercolor;

        .ms_icon {
            vertical-align: center;

            img{
                width: 35px;
                padding: 5px 0px;
            }
        }
    }
</style>