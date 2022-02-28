<template>
  <li class="col-6 col-md-4 col-lg-2 cards">
      <div class="content" :style="{ backgroundImage: `url(https://image.tmdb.org/t/p/w342${film.poster_path})`}">
        {{getTitle(film)}}
        {{film.original_title}}

        <img :src="getFlagUrl(film.original_language)">
        <i v-for="number in 5"
        :key="number"
        class="fa-star"
        :class="starClass(film.vote_average, number)">
        {{film.vote_average}}</i>
      </div>
  </li>
</template>

<script>
export default {
    name: "MyCard",
    props: ["List", "film"],
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
        },
        // richiama il titolo sia dei film che delle serie tv - un unico file per entrambe
        getTitle(title) {
            if (title.title) {
                return title.title
            } else {
                return title.name
            }
        },
        // richiama titolo originale film e serie tv
        getOriginalTitle(title) {
            if (title.title) {
                return title.original_title
            } else {
                return title.original_name
            }
        },
        // stelle
        starClass(vote, number) {
            return number <= Math.ceil(vote / 2) ? "fas" : "far";
        }

    }
}
</script>

<style scoped lang="scss">

@import "../assets/style/variabili.scss";
@import "../assets/style/general.scss";

    li {
        min-height: 300px;
        margin: 30px 0px;

        img {
            width: 50px;
            height: 30px;
        }

        .card {
            background-size: cover;
            background-repeat: no-repeat;
            background-position: center;
        }

        .content {
            height: 100%;
            background-repeat: no-repeat;
            background-size: cover;
            background-position: center;
        }
    }
</style>