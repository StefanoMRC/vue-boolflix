<template>
  <div id="app">
    <HeaderComp @funzRicerca='metodoRicerca'/>
    <MainComp 
    :film="film"
    :serie="serie"
    />
    
  </div>
</template>

<script>
import "bootstrap"
import HeaderComp from './components/header/HeaderComp.vue'
import MainComp from './components/main/MainComp.vue'
import axios from 'axios';


export default {
  name: 'App',
  components: {
    HeaderComp,
    MainComp
  },
  data() {
    return {
      testoRicerca:'',
      apiKey:'95d5ec590516c2769c39d001e98413d8',
      film:[],
      serie:[]
    }
  },
  methods: {
    metodoRicerca(testo){
          this.testoRicerca=testo;
          this.film=[]
          this.serie=[]
          axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${this.apiKey}&language=it&page=1&include_adult=false&query=${this.testoRicerca}`)
      .then((res)=>{
          
          console.log(res.data.results)
          this.film=res.data.results
          console.log(this.film)
          
      }),
      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=${this.apiKey}&language=it&page=1&include_adult=false&query=${this.testoRicerca}`)
      .then((res)=>{
          
          console.log(res.data.results)
          this.serie=res.data.results
          console.log(this.serie)
          
      })
  }}
}
</script>

<style lang="scss">
  @import "bootstrap/dist/css/bootstrap.min.css";
  .bg_custom{
    background: #2e3a46;
  }
  body{
    background: #1e2d3b;
  }
</style>
