<script setup>
import { ref } from 'vue'

const nombre = ref('')
const edad = ref('')
const profesion = ref('')
const mostrarTarjeta = ref(false)

// Arrow Function que genera el mensaje dinámico con Template Literals
const generarTarjeta = () => {
  mostrarTarjeta.value = true
}

const nombreCompleto  = () => `Nombre: ${nombre.value}`
const edadTexto       = () => `Edad: ${edad.value} años`
const profesionTexto  = () => `Profesión: ${profesion.value}`
</script>

<template>
  <div class="border border-gray-200 rounded-2xl p-8">
    <h2 class="text-xl font-bold text-black mb-1 tracking-tight">Ejercicio 2</h2>
    <p class="text-gray-400 text-xs mb-6 uppercase tracking-wider">Tarjeta Dinámica de Usuario</p>

    <!-- Formulario con v-model -->
    <div class="space-y-4">
      <div>
        <label class="block text-xs font-medium text-gray-500 mb-1 uppercase tracking-wider">Nombre</label>
        <input
          v-model="nombre"
          type="text" placeholder="Ej. Carlos"
          class="w-full border border-gray-200 bg-white rounded-lg px-4 py-2.5 text-black text-sm placeholder-gray-300 focus:outline-none focus:border-black transition"
        />
      </div>
      <div>
        <label class="block text-xs font-medium text-gray-500 mb-1 uppercase tracking-wider">Edad</label>
        <input
          v-model="edad"
          type="number" min="0" placeholder="Ej. 22"
          class="w-full border border-gray-200 bg-white rounded-lg px-4 py-2.5 text-black text-sm placeholder-gray-300 focus:outline-none focus:border-black transition"
        />
      </div>
      <div>
        <label class="block text-xs font-medium text-gray-500 mb-1 uppercase tracking-wider">Profesión</label>
        <input
          v-model="profesion"
          type="text" placeholder="Ej. Desarrollador Web"
          class="w-full border border-gray-200 bg-white rounded-lg px-4 py-2.5 text-black text-sm placeholder-gray-300 focus:outline-none focus:border-black transition"
        />
      </div>
    </div>

    <!-- Botón que dispara la tarjeta -->
    <button
      @click="generarTarjeta"
      class="mt-6 w-full bg-black text-white text-sm font-medium py-2.5 rounded-lg hover:bg-gray-800 transition"
    >
      Generar Tarjeta
    </button>

    <div class="border-t border-gray-100 my-6"></div>

    <!-- Tarjeta (v-if) — solo visible tras presionar el botón -->
    <div v-if="mostrarTarjeta" class="border border-gray-200 rounded-xl overflow-hidden">
      <!-- Avatar header strip -->
      <div class="bg-black px-5 py-4 flex items-center gap-4">
        <div class="w-10 h-10 rounded-full bg-white flex items-center justify-center text-black font-bold text-sm shrink-0">
          {{ nombre.charAt(0).toUpperCase() }}
        </div>
        <span class="text-white font-semibold text-sm truncate">{{ nombreCompleto() }}</span>
      </div>
      <!-- Info rows -->
      <div class="divide-y divide-gray-100">
        <div class="flex flex-col px-5 py-3 gap-0.5">
          <span class="text-xs text-gray-400 uppercase tracking-wider">Edad</span>
          <span class="text-sm text-gray-700 font-medium">{{ edadTexto() }}</span>
        </div>
        <div class="flex flex-col px-5 py-3 gap-0.5">
          <span class="text-xs text-gray-400 uppercase tracking-wider">Profesión</span>
          <span class="text-sm text-gray-700 font-medium">{{ profesionTexto() }}</span>
        </div>
      </div>
    </div>

    <p v-if="!mostrarTarjeta" class="text-gray-300 text-xs text-center">
      Completa los datos y presiona el botón para ver la tarjeta.
    </p>
  </div>
</template>
