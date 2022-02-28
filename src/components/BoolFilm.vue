<template>
  <main>
      <div class="container">
           <section>
               <h2>{{compTitle}}</h2>
               <ul class="row g-4">
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

}
</script>

<style scoped lang="scss">
    @import "../assets/style/variabili.scss";
    @import "../assets/style/general.scss";

    h2 {
        font-size: 25px;
        margin-bottom: 30px;
        text-align: left;
    }

    ul {
        list-style: none;
        justify-content: center;
        padding-left: 0px;
    }

    img {
        width: 50px;
        height: 30px;
    }

</style>