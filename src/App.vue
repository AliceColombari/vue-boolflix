<template>
  <div id="app">
    <MyHeader @getEmettiValore="getValoreSelezionato"/>

    <main class=" text-center text-white">
      <div class="container">
        <h4 class="loader-title" v-if="tvList.length == 0">CERCA TRA GLI ORIGINALI BOOLFIX</h4>
        <BoolFilm :List="tvList" compTitle="Serie Tv" v-if="tvList.length > 0"/>
        <BoolFilm :List="filmList" compTitle="Film" v-if="filmList.length > 0"/>
      </div>
    </main>

  </div>
</template>

<script>
// dopo aver inserito nel terminale npm install axios - inserisco la costante per farlo funzionare
const axios = require('axios');
// collegamenti con componenti header e main
import MyHeader from './components/MyHeader.vue'
import BoolFilm from './components/BoolFilm.vue'


export default {
  name: 'App',
  components: {
    MyHeader,
    BoolFilm
  },
  data() {
    return {
      // array lista dei film e serie tv
      tvList: [],
      filmList: [],
    };
  },
  methods: {
    // funzione per richiamare tramite api la lista delle serie tv
    getSerieTvUrl(string){
      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=8a21c58330da7597aae0055b9b34eb91&query=${string}&language=it_IT`)
      .then((risposta) => {
        this.tvList = risposta.data.results
      })
    },
    // funzione per richiamare tramite api la lista dei film
    getFilmUrl(string){
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=8a21c58330da7597aae0055b9b34eb91&query=${string}&language=it_IT`)
      .then((risposta) => {
        this.filmList = risposta.data.results
      })
    },
    // funzione per stampare il valore selezionato nella ricerca
    getValoreSelezionato(value) {
      if(!value) {
        this.tvList = []
        this.filmList = []
        return
      }
      // richiamo le funzioni e il valore
      this.getSerieTvUrl(value);
      this.getFilmUrl(value);
    }
  }
}
</script>

<style lang="scss">

  // riporto il collegamento con il componente scss con regole general
  @import "./assets/style/general.scss";
  @import "./assets/style/variabili.scss";

  main {
    background-color: $mainBg;
    height: calc(100vh - 70px);
    // scroll interna anche alla sezione scelta film / serie tv
    overflow-y: auto;

    .loader-title {
      margin-top: 100px;
    }
  }

</style>
