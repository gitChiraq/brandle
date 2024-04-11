<template>
  <div class="keyboard-row" id="first-row">
    <button @click="sendQ">Q</button>
    <button type="button">W</button>
    <button type="button">E</button>
    <button type="button">R</button>
    <button type="button">T</button>
    <button type="button">Y</button>
    <button type="button">U</button>
    <button type="button">I</button>
    <button type="button">O</button>
    <button type="button">P</button>
  </div>
  <div class="keyboard-row">
    <button type="button">A</button>
    <button type="button">S</button>
    <button type="button">D</button>
    <button type="button">F</button>
    <button type="button">G</button>
    <button type="button">H</button>
    <button type="button">J</button>
    <button type="button">K</button>
    <button type="button">L</button>
  </div>
  <div class="keyboard-row">
    <button type="button">ENTER</button>
    <button type="button">Z</button>
    <button type="button">X</button>
    <button type="button">C</button>
    <button type="button">V</button>
    <button type="button">B</button>
    <button type="button">N</button>
    <button type="button">M</button>
    <button type="button">DEL</button>
  </div>
</template>

<script>
export default {
  methods: {
    sendQ(){
      this.$emit('send-letter',"Q");
    }
  }
}
</script>

<style>
.keyboard-row{
    height: 48px;
    margin: 0 auto;
}
button{
    height: 40px;
    width: 60px;
    margin: 2px;
    background-color: grey;
    color: white;
}

#first-row{
  margin-top:75px;
}

</style>