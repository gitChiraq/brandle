<template>
  <h1>{{ title }}</h1>
  <GameBoard :receivedStringProp="receivedString" />
  <KeyBoard @send-letter="receiveString"/>
</template>

<script>
import GameBoard from './components/GameBoard.vue'
import KeyBoard from './components/KeyboardField.vue'

export default {
  name: 'App',
  components: { GameBoard, KeyBoard},
  data(){
    return{
      receivedString: ''
    }
  },
  methods: {
    receiveString(string){
      this.receivedString = string;
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
