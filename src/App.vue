<script setup>
//import WelcomeItem from './components/WelcomeItem.vue';
import { ref,computed } from 'vue'

const counter= ref(0);
const arrayFavoritos=ref([]); 

const name ='Vue Dinamico';

 const increment = ()=>{
  counter.value ++;
 }

 const disminuir = ()=>{
  counter.value --;
 }
 const reset = ()=>{
  counter.value =0;
 }

 const add =()=> {
  arrayFavoritos.value.push(counter.value);
 }

 const clasComputer = computed(() =>{
 if (counter.value===0){
  return 'zero'
 }
 if(counter.value > 0 ){
  return 'positive'
 }
 if(counter.value < 0){
  return 'negative'
 }

})
  
  const bloquearBtnAdd=computed(() =>{
    const numSerch=arrayFavoritos.value.find((num)=> num=== counter.value);
    console.log(numSerch);
    if(numSerch === 0) return true;
    return numSerch ? true: false;
  })
</script>

 
<template>
 <div class="container tex-center mt-3">
 <h1>Hola {{ name.toUpperCase() }}</h1>
 <h2 :class="clasComputer">{{ counter }}</h2>
 <div class="btn-group">
 <button @click="increment" class="btn btn-success"> Increment</button>
 <button @click="disminuir" class="btn btn-danger"> Decrement</button>
 <button @click="reset" class="btn btn-secondary"> Reset</button>
 <button @click="add" :disabled="bloquearBtnAdd" class="btn btn-primary"> Add</button>
</div>
  <ul class="list-group mt-4">
  <li class="list-group-item" v-for="(num,index) in arrayFavoritos">
   {{ num }}
  </li>
 </ul>
</div>
 </template>


<style>
h1{
  color:red;
  padding: 2px;
}
.positive{
  color :green;
}
.negative {
  color :red;
}
.zero{
  color :peru;
}

</style>
