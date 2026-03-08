<script setup>
import Ejercicio1 from './components/Ejercicio1.vue'
import Ejercicio2 from './components/Ejercicio2.vue'
</script>

<template>
  <div class="min-h-screen bg-white flex flex-col items-center justify-center p-8">
    <h1 class="text-2xl font-bold text-black mb-1 tracking-tight">Parcial DWA</h1>
    <p class="text-gray-400 text-xs mb-10 uppercase tracking-wider">Ejercicios Vue.js</p>

    <div class="w-full max-w-3xl grid grid-cols-1 md:grid-cols-2 gap-6 items-start">
      <Ejercicio1 />
      <Ejercicio2 />
    </div>
  </div>
</template>
