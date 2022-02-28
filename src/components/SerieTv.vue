<template>
  <main>
      <div class="container">
          <ul>
            <li>SERIE TV</li>
            <li v-for="serie in List" :key="serie.id">
                {{serie.name}}
                {{serie.original_name}}
                {{serie.original_language}}
                <img :src="getFlagUrl(serie.original_language)">
                {{serie.vote_average}}
            </li>
           </ul>
      </div>
  </main>
</template>

<script>
export default {
    name: "SerieTv",
    props: ["List"],
    data() {
        return {}
    },
    methods: {
        // richiama bandiera image en e it, in caso contrario, inserisci immagine di errore
        getFlagUrl(flag) {
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