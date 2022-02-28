<template>
  <header>
    <div class="container">
      <h1>BOOLFIX</h1>

      <div class="search">

        <input type="text"
        v-model.trim="value"
        placeholder="Cerca tra gli originali Boolfix">
        
        <button @click="getValore"><i class="fa-solid fa-magnifying-glass"></i></button>

        <i class="fa-solid fa-bell bell"></i>

        <img class="avatar" src="https://upload.wikimedia.org/wikipedia/commons/0/0b/Netflix-avatar.png" alt="">

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
        
        h1 {
        color: $boolfix;
        // eliminato margin-bottom fastidioso
        margin-bottom: 0px;
        }

        .search{
        input {
          width: 200px;
          font-size: 13px;
          border-radius: 5px;
          border: 1px solid $light;
          background-color: $dark;
          color: $light;
          padding: 7px;
          cursor: pointer;
          height: 30px;
        }
        
        button {
          font-size: 20px;
          border: none;
          color: $light;
          background-color: $dark;
          margin: 0px 15px;
          line-height: 30px;
          vertical-align: middle;
        }

        .bell {
          margin-right: 15px;
          font-size: 20px;
          color: $light;
          line-height: 30px;
          vertical-align: middle;
        }

        .avatar {
          height: 25px;
          border-radius: 5px;
          line-height: 30px;
          vertical-align: middle;
        }
      }

      }
    }

</style>
