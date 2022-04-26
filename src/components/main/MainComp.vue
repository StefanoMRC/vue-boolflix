<template>
<div class="bg_custom2">
  <div class="container p-5">
    
   <FilmComp :film="film"/>
   <SerieComp :serie='serie'/>
  </div>
</div>

</template>

<script>
import FilmComp from './componenti film&serie/FilmComp.vue'
import SerieComp from './componenti film&serie/SerieComp.vue'
export default {
  name: 'MainComp',
  components:{
    FilmComp,
    SerieComp
  },
  props:{
    film:Array,
    serie:Array
  }
  
   
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
