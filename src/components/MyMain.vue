<template>
  <main>
      <div class="container">
          <!-- milestone 1 -->
          <!-- stampa valori film trovati  -->
          <ul>
            <li v-for="film in filmList" :key="film.id">
                {{film.title}}
                {{film.original_title}}
                {{film.original_language}}
                {{film.vote_average}}
            </li>
           </ul>
           <!-- fine milestone 1 -->
      </div>
  </main>
</template>

<script>
export default {
    name: "MyMain",
    props: ["filmList"],
}
</script>

<style scoped lang="scss">
    @import "../assets/style/variabili.scss";

    ul {
        padding-top: 20px;
    }

</style>