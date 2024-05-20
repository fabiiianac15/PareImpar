<template>
    <div class="py-8 px-10">
      <div class="flex gap-4 mb-4">
        <button @click="clasificarPar" class="w-1/5 bg-red-600 text-white font-bold py-2 rounded">Par</button>
        <button @click="clasificarImpar" class="w-1/5 bg-green-600 text-white font-bold py-2 rounded">Impar</button>
        <input v-model="agregar" type="number" class=" w-2/5  placeholder:p-2" placeholder="Agregar Número">
        <button class=" bg-white rounded p-2" @click="agregarNumeros" >Agregar</button>
      </div>
      <div class="flex gap-4">
        <div class="w-1/2 bg-white/80 p-4 rounded shadow">
          <h3 class="text-lg font-bold mb-2">Números pares:</h3>
          <div v-for="(number, index) in pares" :key="index" class="bg-blue-100 px-2 py-1 mb-1 rounded">
            {{ number }}
          </div>
        </div>
        <div class="w-1/2 bg-white/80 p-4 rounded shadow">
          <h3 class="text-lg font-bold mb-2">Números impares:</h3>
          <div v-for="(number, index) in impares" :key="index" class="bg-yellow-100 px-2 py-1 mb-1 rounded">
            {{ number }}
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const numbers = ref([]);
  const agregar = ref ([]);
  const pares = ref([]);
  const impares = ref([]);
  
  function esPar(num) {
    return num % 2 === 0;
  }
  
  function esImpar(num) {
    return num % 2 !== 0;
  }
  
  function clasificarPar() {
    pares.value = numbers.value.filter(esPar);
  }
  
  function clasificarImpar() {
    impares.value = numbers.value.filter(esImpar);
  }

  function agregarNumeros (){
    numbers.value.push(agregar.value)
  }
  </script>
  