<template>
  <header>
    <div class="container">
      <h1>BOOLFIX</h1>
      <div class="search">
        <!-- milestone 1 -->
        <!-- ricerca in input il valore del film e al click sul btn stampa valore -->
        <input type="text" v-model="value" placeholder="Seleziona un film">
        <button @click="getValore">CERCA</button>
        <!-- fine milestone 1 -->
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'MyHeader',
  data() {
    return {
      value: "",
    }
  },
  methods: {
    getValore() {
      // creo pulsante attraverso $emit
      this.$emit("getEmettiValore", this.value);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    @import "../assets/style/variabili.scss";
    header {
      background-color: $dark;
      height: 70px;
      
      .container {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 30px;
        
        h1 {
        color: $boolfix;
      }

      .search{
        input {
          border-radius: 5px #000;
          padding: 7px;
          cursor: pointer;
          margin-right: 10px;
        }

        button {
          padding: 7px;
          border-radius: 5px #000;
        }
      }
      }
    }

</style>
