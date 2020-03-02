<template>
  <div id="app">
    <h1>v-minesweeper</h1>
    <p>This should soon be a Minesweeper game implemented in Vue</p>
    <minesweeper-game />
  </div>
</template>

<script>
import MinesweeperGame from './components/MinesweeperGame'

export default {
  name: 'App',
  components: { MinesweeperGame }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
