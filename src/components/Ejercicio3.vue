<script setup>
import { ref } from 'vue'

// Arreglo de objetos con productos
const productos = ref([
  { id: 1, nombre: 'Laptop',   precio: 800 },
  { id: 2, nombre: 'Mouse',    precio: 20  },
  { id: 3, nombre: 'Teclado',  precio: 35  },
  { id: 4, nombre: 'Monitor',  precio: 250 },
  { id: 5, nombre: 'Audífonos',precio: 60  },
])

// Arrow Function que genera el formato de texto con Template Literals
const formatoProducto = (producto) =>
  `Producto: ${producto.nombre} — Precio: $${producto.precio}`
</script>

<template>
  <div class="border border-gray-200 rounded-2xl p-8">
    <h2 class="text-xl font-bold text-black mb-1 tracking-tight">Ejercicio 3</h2>
    <p class="text-gray-400 text-xs mb-6 uppercase tracking-wider">Lista Dinámica de Productos</p>

    <!-- v-for: recorre el arreglo de productos -->
    <ul class="divide-y divide-gray-100">
      <li
        v-for="producto in productos"
        :key="producto.id"
        class="flex items-center justify-between py-3"
      >
        <!-- Nombre del producto -->
        <div class="flex items-center gap-3">
          <span class="w-8 h-8 rounded-lg bg-gray-100 flex items-center justify-center text-xs font-bold text-gray-500">
            {{ producto.nombre.charAt(0) }}
          </span>
          <span class="text-sm font-medium text-gray-800">{{ producto.nombre }}</span>
        </div>

        <!-- Precio formateado con Template Literal via arrow function -->
        <span class="text-sm text-gray-500">${{ producto.precio }}</span>
      </li>
    </ul>

    <!-- Texto generado por la Arrow Function con Template Literals -->
    <div class="mt-6 border-t border-gray-100 pt-5 space-y-1">
      <p class="text-xs text-gray-400 uppercase tracking-wider mb-2">Formato de texto</p>
      <p
        v-for="producto in productos"
        :key="`texto-${producto.id}`"
        class="text-xs text-gray-500"
      >
        {{ formatoProducto(producto) }}
      </p>
    </div>
  </div>
</template>
