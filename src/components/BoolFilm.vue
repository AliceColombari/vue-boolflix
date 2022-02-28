<template>
  <main>
      <div class="container">

          <!-- <ul>
            <li>{{compTitle}}</li>
            <li v-for="film in List" :key="film.id">
                {{getTitle(film)}}
                {{film.original_title}}

                <img :src="getFlagUrl(film.original_language)">
                <img :src="`https://image.tmdb.org/t/p/w342${film.backdrop_path}`">
                
                <i v-for="(star, index) in vote" 
                :key="index" class="far fa-star" 
                :class="{fas: isIndex(film.vote_average, index)}">
                {{index + 1}}</i>
                {{film.vote_average}}

            </li>
           </ul> -->

           <section>
               <h2>{{compTitle}}</h2>
               <ul class="row px-4">
                   <MyCard v-for="film in List" :key="film.id" :List="List" :film="film"/>
               </ul>
           </section>
      </div>
  </main>
</template>

<script>

import MyCard from "./MyCard.vue"

export default {
    name: "BoolFilm",
    props: ["List", "compTitle"],
    components: {
        MyCard
    },
    data() {
        return {
            // votazione stelle
            rateValue: 0,
            // vote: ["1", "2", "3", "4", "5"]
        }
    },
    // methods: {
    //     getFlagUrl(flag) {
    //          // richiama bandiera image en e it, in caso contrario, inserisci immagine di errore
    //         if (flag == "en") {
    //             return require("../assets/img/en.png");
    //         } else if (flag == "it") {
    //             return require("../assets/img/it.png");
    //         } else {
    //             return "https://developers.google.com/maps/documentation/streetview/images/error-image-generic.png";
    //         }
    //     },
    //     // richiama il titolo sia dei film che delle serie tv - un unico file per entrambe
    //     getTitle(title) {
    //         if (title.title) {
    //             return title.title
    //         } else {
    //             return title.name
    //         }
    //     },
    //     // richiama titolo originale film e serie tv
    //     getOriginalTitle(title) {
    //         if (title.title) {
    //             return title.original_title
    //         } else {
    //             return title.original_name
    //         }
    //     },
    //     // funzione per votazione stelle
    //     isIndex(vote, index) {
    //         const roundedVote = Math.ceil(vote / 2);
    //         if (roundedVote >= index + 1) {
    //             return true
    //         } else {
    //             return false
    //         }
    //     }
    // }

}
</script>

<style scoped lang="scss">
    @import "../assets/style/variabili.scss";
    @import "../assets/style/general.scss";

    ul {
        list-style: none;
        justify-content: center;
    }

    img {
        width: 50px;
        height: 30px;
    }

</style>