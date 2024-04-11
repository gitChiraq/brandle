<template>
  <div class="row">
    <div class="element1">{{ receivedStringProp }}</div>
    <div class="element2">A</div>
    <div class="element3"></div>
    <div class="element4"></div>
    <div class="element5"></div>
  </div>
  <div class="row">
    <div class="element1"></div>
    <div class="element2"></div>
    <div class="element3"></div>
    <div class="element4"></div>
    <div class="element5"></div>
  </div>
  <div class="row">
    <div class="element1"></div>
    <div class="element2"></div>
    <div class="element3"></div>
    <div class="element4"></div>
    <div class="element5"></div>
  </div>
  <div class="row">
    <div class="element1"></div>
    <div class="element2"></div>
    <div class="element3"></div>
    <div class="element4"></div>
    <div class="element5"></div>
  </div>
  <div class="row">
    <div class="element1"></div>
    <div class="element2"></div>
    <div class="element3"></div>
    <div class="element4"></div>
    <div class="element5"></div>
  </div>
</template>

<script>
//import App from '@/App.vue';

export default {
  props: {
    receivedStringProp: String
  }
}
</script>

<style>
div{
  
  color:white;
  text-align: center;
  vertical-align: middle;
}
.row{
    height: 70px;
    width: 400px;
    
    margin: 0 auto;

}

.element1{
  line-height:70px;
  display:inline-block;
  height: 60px;
  width: 60px;
  margin: 3px;
  border:1px solid grey;
}
.element2{
  line-height:70px;
  display:inline-block;
  height: 60px;
  width: 60px;
  margin: 3px;
  border:1px solid grey;
}
.element3{
  line-height:70px;
  display:inline-block;
  height: 60px;
  width: 60px;
  margin: 3px;
  border:1px solid grey;
}
.element4{
  line-height:70px;
  display:inline-block;
  height: 60px;
  width: 60px;
  margin: 3px;
  border:1px solid grey;
}
.element5{
  line-height:70px;
  display:inline-block;
  height: 60px;
  width: 60px;
  margin: 3px;
  border:1px solid grey;
}

</style>