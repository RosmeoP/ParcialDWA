<script setup>
import { ref, computed } from 'vue'

const nota1 = ref('')
const nota2 = ref('')
const nota3 = ref('')

const calcularPromedio = () => {
  const n1 = parseFloat(nota1.value) || 0
  const n2 = parseFloat(nota2.value) || 0
  const n3 = parseFloat(nota3.value) || 0
  return ((n1 + n2 + n3) / 3).toFixed(2)
}

const promedio = computed(() => calcularPromedio())

const notasIngresadas = computed(() =>
  nota1.value !== '' && nota2.value !== '' && nota3.value !== ''
)

const mensajeResultado = computed(() =>
  `El promedio del estudiante es ${promedio.value} y su estado es: ${parseFloat(promedio.value) >= 6 ? 'Aprobado' : 'Reprobado'}`
)
</script>

<template>
  <div class="border border-gray-200 rounded-2xl p-8">
    <h2 class="text-xl font-bold text-black mb-1 tracking-tight">Ejercicio 1</h2>
    <p class="text-gray-400 text-xs mb-6 uppercase tracking-wider">Calculadora de Promedio</p>

    <div class="space-y-4">
      <div>
        <label class="block text-xs font-medium text-gray-500 mb-1 uppercase tracking-wider">Nota 1</label>
        <input
          v-model="nota1"
          type="number" min="0" max="10" step="0.1" placeholder="0.0"
          class="w-full border border-gray-200 bg-white rounded-lg px-4 py-2.5 text-black text-sm placeholder-gray-300 focus:outline-none focus:border-black transition"
        />
      </div>
      <div>
        <label class="block text-xs font-medium text-gray-500 mb-1 uppercase tracking-wider">Nota 2</label>
        <input
          v-model="nota2"
          type="number" min="0" max="10" step="0.1" placeholder="0.0"
          class="w-full border border-gray-200 bg-white rounded-lg px-4 py-2.5 text-black text-sm placeholder-gray-300 focus:outline-none focus:border-black transition"
        />
      </div>
      <div>
        <label class="block text-xs font-medium text-gray-500 mb-1 uppercase tracking-wider">Nota 3</label>
        <input
          v-model="nota3"
          type="number" min="0" max="10" step="0.1" placeholder="0.0"
          class="w-full border border-gray-200 bg-white rounded-lg px-4 py-2.5 text-black text-sm placeholder-gray-300 focus:outline-none focus:border-black transition"
        />
      </div>
    </div>

    <div class="border-t border-gray-100 my-6"></div>

    <!-- Resultado (v-if) -->
    <div v-if="notasIngresadas" class="border border-gray-200 rounded-xl p-5 space-y-3">
      <p class="text-gray-700 text-sm leading-relaxed">{{ mensajeResultado }}</p>
      <span
        v-if="parseFloat(promedio) >= 6"
        class="inline-block bg-black text-white text-xs font-medium px-3 py-1 rounded-full"
      >✓ Aprobado</span>
      <span
        v-if="parseFloat(promedio) < 6"
        class="inline-block border border-black text-black text-xs font-medium px-3 py-1 rounded-full"
      >✗ Reprobado</span>
    </div>

    <p v-if="!notasIngresadas" class="text-gray-300 text-xs text-center">
      Completa las tres notas para ver el resultado.
    </p>
  </div>
</template>
