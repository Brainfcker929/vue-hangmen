<template>
  <div class="container">
    <Header :lives="lives" />
    <Board v-model:lives.sync="lives" />
  </div>
</template>

<script>
import Header from "./components/Header";
import Board from "./components/Board";

export default {
  name: "App",
  components: {
    Header,
    Board,
  },
  data() {
    return {
      lives: 10,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  margin-top: 60px;
}

html {
  background-color: crimson;
  color: white;
}

.container {
  margin: auto;
  width: 50%;
  text-align: center;
}

.letter {
  margin: 0.5rem;
  background-color: white;
  width: 30px;
  height: 30px;
  border: solid 2px black;
  color: black;
  line-height: 30px;
}

.solution {
  justify-content: center;
  display: flex;
  flex-wrap: wrap;
  align-items: flex-start;
}

.alphabet {
  display: flex;
  flex-wrap: wrap;
  align-items: flex-start;
}
</style>
