<template>
  
    <div class="col-2 g-3">
      <img class="img-fluid" :src="`https://image.tmdb.org/t/p/w500/${img}`" alt="">
    </div>
  
</template>

<script>
export default {
  name: 'CardComp',
  props: {
    img:String
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
