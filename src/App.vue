<template>
  <h2>La Cena de hoy es {{ contador + 1 }}: {{ nombre }}</h2>\
  <h3 class="Precio"> Precio ${{ productos[contador].precio }}
      <div>
        <p :class="Ingredientes"> Ingredientes = {{ productos[contador].ingredientes}}</p>
        </div>
      <div v-if="productos[contador].findesemana" class="LosFinesdeSemana">
            (Disponible solos los fines de semana)
      </div>
      <div v-else class="todosLosDias">
            (Disponible solo en la semana)
      </div>
  </h3>
  <img :src="productos[contador].imagen" alt="Imagen del producto" />

  <button @click="siguiente">Siguiente ({{ contador + 1 }}/{{ total }})</button>
</template>

<script setup>
import { ref, computed } from "vue";
import { productos } from "./data.js";

const contador = ref(0); // Contador Reactivo
const total = productos.length; // Asegúrate de que productos está definido correctamente

const siguiente = () => {
  contador.value++;
  if (contador.value >= total) {
    contador.value = 0; // Reinicia al primer producto si se llega al final
  }
};

// Propiedad computada para obtener el nombre formateado
const nombre = computed(() => {
  const Elnombre = productos[contador.value].nombre.toLowerCase();
  return Elnombre.charAt(0).toUpperCase() + Elnombre.slice(1);
});
</script>

<style scoped>

.todosLosDias{
    color: green;
}

.LosFinesdeSemana{
    color: red;
}
.Precio{
    font-size: 30px;
}

</style>
