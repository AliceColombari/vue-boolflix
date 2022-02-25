<template>
  <div id="app">
    <MyHeader @getEmettiValore="getValoreSelezionato"/>
    <MyMain :filmList="filmList"/>
  </div>
</template>

<script>
// dopo aver inserito nel terminale npm install axios - inserisco la costante per farlo funzionare
const axios = require('axios');
// collegamenti con componenti header e main
import MyHeader from './components/MyHeader.vue'
import MyMain from './components/MyMain.vue'


export default {
  name: 'App',
  components: {
    MyHeader,
    MyMain
  },
  data() {
    return {
      // array lista dei film 
      filmList: [],
      cercaValore: "",
    };
  },
  methods: {
    // funzione che richiama attraverso axios api dei film
    getUrl(string) {
      // riporto il valore string come valore della query in modo tale che mi riporti tutti i valori di tutti i film
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=8a21c58330da7597aae0055b9b34eb91&query=${string}&language=it_IT`)
      .then((risposta) => {
        this.filmList = risposta.data.results;
      });
    },
    // funzione che ricerca il nome/genere selezionato in input all'interno della funzione getUrl(axios api)
    getValoreSelezionato(value) {
      this.cercaValore = value;
      this.getUrl(this.cercaValore);
    }
  }
}
</script>

<style lang="scss">

  // riporto il collegamento con il componente scss con regole general
  @import "./assets/style/general.scss";

</style>
