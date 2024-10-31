<!--
<template>
  <!-- Pintando en la web -->
  <h1 v-bind:style="Mycolor">Hola soy {{ Nombre }} y tengo {{ Edad }}</h1>
  <h2 v-bind:class="selector">Hola soy {{ Nombre }} y tengo {{ Edad }}</h2>

  <div>
    <button @click="decremento">-</button>
    <span :class="NumberColor">{{ contador }}</span>
    <button @click="incremento">+</button>
  </div>

  <!-- Directivas if else -->
  <div v-if="contador < 0"> 
    <span>Decremento</span>
  </div>

  <div v-else-if="contador > 0"> 
    <span>Incremento</span>
  </div>

  <div v-else> 
    <span>Numero 0</span>
  </div>
</template>
-->

<script setup>
// importaciones y definición de variables y métodos
import { ref } from "vue"

/* Definición de variables */
const NumberColor = ref("green")
const contador = ref(0)
const Nombre = "Patricio"
const Edad = 26
const Mycolor = "color:green;font-size:3em"
const selector = "azul"

/* Función para decrementar el contador */
const decremento = () => {
  contador.value--
  if (contador.value < 0) {
    NumberColor.value = "red"
  }
}

/* Función para incrementar el contador */
const incremento = () => {
  contador.value++
  if (contador.value >= 0) {
    NumberColor.value = "green"
  }
}
</script>

<style scoped>
/* Estilos */
.azul {
  color: blue;
}
.green {
  color: green;
}
.red {
  color: red;
}
span {
  font-size: 100px;
}
</style>
