<template>
  <main>
      <div class="container">
          <ul>
            <li>FILM</li>
            <li v-for="film in List" :key="film.id">
                {{film.title}}
                {{film.original_title}}
                {{film.original_language}}
                <img :src="getFlagUrl(film.original_language)">
                {{film.vote_average}}
            </li>
           </ul>
      </div>
  </main>
</template>

<script>
export default {
    name: "BoolFilm",
    props: ["List"],
    methods: {
        getFlagUrl(flag) {
             // richiama bandiera image en e it, in caso contrario, inserisci immagine di errore
            if (flag == "en") {
                return require("../assets/img/en.png");
            } else if (flag == "it") {
                return require("../assets/img/it.png");
            } else {
                return "https://developers.google.com/maps/documentation/streetview/images/error-image-generic.png";
            }
        }
    }

}
</script>

<style scoped lang="scss">
    @import "../assets/style/variabili.scss";

    ul {
        padding-top: 20px;

        li:first-child {
            font-weight: bold;
        }
    }

</style>