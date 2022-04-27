<template>

  <div class="col-2 g-2 mx-2 card_principale p-0">
    <div class="flip-card-inner">
      <div class="card_foto">
        <!-- <img :src="`https://image.tmdb.org/t/p/w500/${img}`" alt=""> -->
        <img :class="(img ==null)? `bg_custom p-2`:''" :src="(img ==null)? `https://i.ebayimg.com/images/g/Fv8AAOSwfIVgCawI/s-l300.png`: `https://image.tmdb.org/t/p/w500/${img}`" alt="">
      </div>

      <div class="card_info d-flex flex-column p-2 align-items-center">
        <div class="p-1 text-center">
          <h5>Titolo originale:</h5>
          <span>{{titolo}}</span>
        </div>
        <div class="text-center">
          <h5 class="me-1">Lingua originale:</h5>
          <span class="bandiera text-center "
            :class="(lingua=='en')?'bandieraIng': (lingua=='it') ? 'bandieraIta': 'noBandiera'"></span>
        </div>
        <div class="p-1 text-center">
          <h5>Valutazione</h5>
          <!-- <span v-for="(element,index) in pippo()" :key="index">{{element}}</span> -->
          <div class="d-flex">
            <img class="stella" v-for="(element,index) in stellaPiena()" :key="index" :src="element" alt="">
            <img class="stella" v-for="(elem,index) in stellaVuota()" :key="'A'+index" :src="elem" alt="">
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

  </div>

</template>

<script>
  import img1 from '../../../assets/img/stellapiena.png'
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


      }
    },
    methods: {
      stellaPiena: function () {
        let arrayStar = []
        for (let i = 0; i < this.numero; i++) {
          arrayStar.push(img1)
        }
        return arrayStar
      },
      stellaVuota: function () {
        let arrayStar2 = []
        for (let i = this.numero; i < 5; i++) {
          arrayStar2.push(img2)
        }
        return arrayStar2
      }



    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .card_principale {
    background-color: transparent;
    perspective: 1000px;
    width: 220px;
    height: 300px;

    .flip-card-inner {
      position: relative;
      width: 100%;
      height: 100%;
      text-align: center;
      transition: transform 0.8s;
      transform-style: preserve-3d;

      .card_foto {
        position: absolute;
        width: 100%;
        height: 100%;
        -webkit-backface-visibility: hidden;
        /* Safari */
        backface-visibility: hidden;

        img {
          height: 100%;
          width: 100%;
          border-radius: 20px;
        }

      }

      .card_info {
        height: 100%;
        width: 100%;
        position: absolute;
        width: 100%;
        height: 100%;
        -webkit-backface-visibility: hidden;
        /* Safari */
        backface-visibility: hidden;
        background: #2e3a46;
        color: white;
        overflow-y: auto;

        z-index: 1;
        transform: rotateY(180deg);
        border-radius: 20px;

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

        .bandiera {
          display: inline-block;
          height: 30px;
          width: 30px;
        }

        .bandieraIta {
          background-image: url('../../../assets/img/itas.png');
          background-size: contain;
          background-repeat: no-repeat;
          background-position: center;
        }

        .bandieraIng {
          background-image: url('../../../assets/img/eng.png');
          background-size: contain;
          background-repeat: no-repeat;
          background-position: center;
        }

        .noBandiera {
          background-image: url('../../../assets/img/no-flag.png');
          background-size: contain;
          background-repeat: no-repeat;
          background-position: center;
        }
      }
    }
  }

  .card_principale:hover .flip-card-inner {
    transform: rotateY(180deg);
  }

  .card_info::-webkit-scrollbar {
    display: none;
  }
  
</style>