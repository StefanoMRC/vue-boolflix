<template>
  <div class="row mt-3" >
  <h1 class="text-uppercase text-white" v-if=" film.length >0">film:</h1>
   <CardComp 
   v-for="(elem,index) in film" :key="index"
   :img="elem.poster_path"
   :voto='elem.vote_average'
   :trama='elem.overview'
   :titolo='elem.original_title'
   :lingua='elem.original_language'
   />
  </div>
</template>

<script>
import CardComp from './CardComp.vue'


export default {
  components:{
    CardComp
  },
  name: 'FilmComp',
  props:{
    film:Array
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
