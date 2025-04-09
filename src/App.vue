<template>
  <div id="app">
    <h1>♟ Jeu d'Échecs</h1>
    <ChessBoard />
  </div>
</template>

<script>
import ChessBoard from './components/ChessBoard.vue';

export default {
  name: 'App',
  components: {
    ChessBoard
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  padding: 2rem;
}
</style>
