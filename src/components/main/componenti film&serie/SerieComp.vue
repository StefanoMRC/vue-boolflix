<template>
  <div class="row flex-wrap mt-5" >
  <h1 class="text-uppercase text-white" v-if=" serie.length >0">serie:</h1>
   <CardComp 
   v-for="(element,index) in serie" :key="index"
   :img="element.poster_path"
   :voto='element.vote_average'
   :trama='element.overview'
   :titolo='element.original_name'
   :lingua='element.original_language'
   />
  </div>
</template>

<script>
import CardComp from './CardComp.vue'
export default {
  components:{
    CardComp
  },
  name: 'SerieComp',
    props:{
      serie:Array
    }



}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
