<template>
  <li class="col col-md-6 col-lg-4 col-xl-3 cards overflow">
      <div class="content" :style="{ backgroundImage: getBackgroundImage(film.poster_path)}">
          <div class="description">
              <ul>
                  <li>
                      TITOLO: {{getTitle(film)}}
                  </li>
                  <li>
                      TITOLO ORIGINALE: {{getOriginalTitle(film)}}
                  </li>
                  <li>
                      LINGUA ORIGINALE: <img :src="getFlagUrl(film.original_language)" alt="">
                  </li>
                  <li>
                      VOTO:
                      <i class="fa-star" v-for="number in 5" :key="number" :class="starClass(film.vote_average, number)"></i>
                  </li>
                  <li>
                      TRAMA: {{film.overview}}
                  </li>
              </ul>
          </div>
      </div>
  </li>
</template>

<script>
export default {
    name: "MyCard",
    props: ["List", "film"],
    data() {
        return {
            visible: false
        }
    },
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
        },
        // image 
        getBackgroundImage(path) {
            if (path && this.visible == false) {
                
                return `url(https://image.tmdb.org/t/p/w342${path})` 

            } else {
                
                return `url(https://www.publicdomainpictures.net/pictures/280000/nahled/not-found-image-15383864787lu.jpg)`
               
            }
        }
    }
}
</script>

<style scoped lang="scss">

@import "../assets/style/variabili.scss";
@import "../assets/style/general.scss";

    .cards {
        height: 300px;
        margin: 20px 0px;

        img {
            width: 20px;
            height: 13px;
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
            border-radius: 5px;
            overflow-y: auto;
            position: relative;

            .description {
                background-color: $dark;
                font-size: 13px;
                display: none;
                min-height: 300px;
                padding: 10px;
                position: absolute;
                left: 0;
                right: 0;
                top: 0;

                ul {
                    list-style: none;
                    // eliminato padding fastidioso
                    padding: 0;

                    li {
                    margin: 5px 0px;
                    text-align: left;
                    }
                }
            }

        }

          .content:hover .description {
                display: block;
                cursor: pointer;
                border: 3px solid $light;
                border-radius: 5px;
            }
    }
</style>