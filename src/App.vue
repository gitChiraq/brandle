<template>
  <h1>{{ title }}</h1>
  <GameBoard />
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import GameBoard from './components/GameBoard.vue'

export default {
  name: 'App',
  components: { GameBoard },
  data(){
    return{
      title: 'brandle'
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ABB2B9;
  margin-top: 60px;
}
</style>
