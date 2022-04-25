<template>
  
    <div class="col-2 g-3 mx-2 card_principale p-0">
      <img  :src="`https://image.tmdb.org/t/p/w500/${img}`" alt="">
      <div class="card_info d-flex flex-column p-2">
        <div class="p-1"><h5>Titolo originale:</h5><span>{{titolo}}</span></div>
        <div class="p-1"><h5>Valutazione</h5><span>{{numero}}</span></div>
        <div class="p-1" v-if="trama !=''" ><h5>Trama:</h5><span>{{trama}}</span></div>
        <div class="p-1" v-else ><h5>Trama:</h5><span>Trama non disponibile</span></div>
      </div>
    </div>
  
</template>

<script>
export default {
  name: 'CardComp',
  props: {
    img:String,
    voto:Number,
    trama:String,
    titolo:String
  },
  data() {
    return {
      numero:Math.round(this.voto/2),
      arrayStar:[]
    }
  },
  methods: {

}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .card_principale{
    position: relative;
    
    img{
      height: 100%;
      width: 100%;
      position: relative;
      z-index: 2;
      top: 0;
      left: 0;
      bottom: 0;
      right: 0;
    }
    .card_info{
      height: 100%;
      width: 100%;
      position:absolute;
      top: 0px;
      right: 0px;
      bottom: 0px;
      left: 0;
      background: rgba(0, 0, 0, 0.507);
      color: white;
      overflow-y:auto;
      z-index: 1;
      h5{
        margin: 0;
      }
    }
    
      
    
  }
  .card_principale:hover .card_info{ z-index: 3;}
</style>
