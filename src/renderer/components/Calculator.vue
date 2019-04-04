<template>
  <div id="wrapper">
    <div class='title'>
    Kalkulator
    </div>
    <div class="content">
    {{ math }} &nbsp;
    </div>
    <div class="numbers">
     <div v-for="i in 10" class="number" @click="setNumber(i - 1)">
      {{ i - 1 }} &nbsp;
     </div>
     <div class="number" @click="setNumber('+')">
       +
     </div>
      <div class="number" @click="setNumber('-')">
       -
     </div>
      <div class="number" @click="setNumber('X')">
       X
     </div>
      <div class="number" @click="setNumber('/')">
       /
     </div>
      <div class="number" @click="createMath()">
       =
     </div>
      <div class="number" @click="cleanMath()">
       C
     </div>
    </div>
  </div>
</template>

<script>
 import stringMath from 'string-math'
  export default {
    name: 'Calculator',
    data(){
     return {
       math:""
     }
    },
    methods: {
      setNumber(i){
        this.math = this.math.split("=")[0] + i;
      },
      cleanMath(){
        this.math = "";
      },
      createMath(){
         let math = this.math.replace("X","*");
         if( this.math.length > 13 ) {
           this.math = stringMath(this.math);
         } else {
           this.math = this.math + "=" + stringMath(math) //1
         }
      }
    }
  }
</script>

<style>
  @import url('https://fonts.googleapis.com/css?family=Source+Sans+Pro');
  body {
    margin:0;
     color:white;
     font-size:50px;
     font-family: 'Source Sans Pro', sans-serif;
       background-color:#63615d;
  }
  .title {
    background-color:#d69a0e;
    width:100%;
    padding-top:1vh;
    height:12%;
    border-bottom:1px solid black;
    text-align:center;
  }
  .content {
    background-color:#444340;
    width:100%;
    height:12%;
    text-align:right;
  }
   .numbers {
    background-color:#63615d;
    width:100%;
    height:76%;
  }
  .numbers > .number {
    float:left;
    border:1px solid #7f7d7a;
    width:19%;
    text-align:center;
    background-color:#6d6b69;
  }

</style>
