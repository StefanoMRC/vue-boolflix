<template>

  <div class="col-2 g-3 mx-2 card_principale p-0">
    <img :src="`https://image.tmdb.org/t/p/w500/${img}`" alt="">
    <div class="card_info d-flex flex-column p-2 align-items-center">
      <div class="p-1 text-center">
        <h5>Titolo originale:</h5>
        <span>{{titolo}}</span>
      </div>
      <div class="text-center">
        <h5 class="me-1">Lingua originale:</h5>
        <span class="bandiera text-center " :class="(lingua=='en')?'bandieraIng': (lingua=='it') ? 'bandieraIta': 'noBandiera'"></span>
      </div>
      <div class="p-1 text-center">
        <h5>Valutazione</h5>
        <!-- <span v-for="(element,index) in pippo()" :key="index">{{element}}</span> -->
        <div class="d-flex">
          <img class="stella" v-for="(element,index) in stellaPiena()" :key="index" :src="element" alt="">
          <img class="stella" v-for="(elem,index) in stellaVuota()" :key="index" :src="elem" alt="">
        </div>
      </div>
      <div class="p-1 text-center" v-if="trama !=''">
        <h5>Trama:</h5>
        <span class="testo">{{trama}}</span>
      </div>
      <div class="p-1 text-center" v-else>
        <h5>Trama:</h5>
        <span class="testo">Trama non disponibile</span>
      </div>
    </div>
  </div>

</template>

<script>
  import img from '../../../assets/img/stellapiena.png'
  import img2 from '../../../assets/img/stellavuota.png'
  export default {
    name: 'CardComp',
    props: {
      img: String,
      voto: Number,
      trama: String,
      titolo: String,
      lingua: String
    },
    data() {
      return {
        numero: Math.round(this.voto / 2),
        arrayStar: [],
        arrayStar2: []
      }
    },
    methods: {
      stellaPiena: function () {
        this.arrayStar = []
        for (let i = 0; i < this.numero; i++) {
          this.arrayStar.push(img)
        }
        return this.arrayStar
      },
      stellaVuota: function () {
        this.arrayStar2 = []
        for (let i = this.numero; i < 5; i++) {
          this.arrayStar2.push(img2)
        }
        return this.arrayStar2
      }



    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .card_principale {
    position: relative;

    img {
      height: 100%;
      width: 100%;
      position: relative;
      z-index: 2;
      top: 0;
      left: 0;
      bottom: 0;
      right: 0;
    }

    .card_info {
      height: 100%;
      width: 100%;
      position: absolute;
      top: 0px;
      right: 0px;
      bottom: 0px;
      left: 0;
      background: rgba(0, 0, 0, 0.507);
      color: white;
      overflow-y: auto;
      z-index: 1;

      h5 {
        margin: 0;
        
      }

      .testo {
        text-align: justify;
        display: inline-block;
      }

      .stella {
        height: 24px;
        width: 24px;
        filter: invert(2);
      }
      .bandiera{
        display: inline-block;
        height: 30px;
        width: 30px;
      }
      .bandieraIta{
        background-image:url('../../../assets/img/itas.png');
        background-size: contain;
        background-repeat: no-repeat;
        background-position: center;
      }
      .bandieraIng{
        background-image:url('../../../assets/img/eng.png');
        background-size: contain;
        background-repeat: no-repeat;
        background-position: center;
      }
      .noBandiera{
        background-image:url('../../../assets/img/no-flag.png');
        background-size: contain;
        background-repeat: no-repeat;
        background-position: center;
      }
    }
  }

  .card_principale:hover .card_info {
    z-index: 3;
  }
</style>