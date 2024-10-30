// Pintando en la web
<template>
  <h1 v-bind:style="Mycolor">Hola soy {{ Nombre }} y tengo {{ Edad }}</h1>
    <h2 v-bind:class="selector">Hola soy {{ Nombre }} y tengo {{ Edad }}</h2>

  <div>
    <button @click="decremento">-</button>
    <span :class="NumberColor">{{ contador }}</span>
    <button @click="incremento">+</button>
  </div>
</template>

<script setup>
import {ref} from "vue"

const NumberColor = ref("green")
const contador= ref(0)
const Nombre = "Patricio";
const Edad = 26;
const Mycolor = "color:green;font-size:3em";
const selector = "azul"

const decremento = () => {
    contador.value--
    if(contador.value < 0) {
      NumberColor.value = "red"
    }
}
const incremento = () => {
    contador.value++
    if(contador.value >= 0) {
      NumberColor.value = "green"
    }
}
</script>

// Estilos
<style scoped>
.azul {
  color: blue;
}
.green {
  color: green
}
.red {
  color: red;
}
span {
  font-size: 100px;
}
</style>
