<template>
  <div class="contenedor">
    <h1>Juego 3 en Raya</h1>
    <div class="fila" v-for="(row, rowIndex) in tablero" :key="rowIndex">
      <CasillaComponent 
        v-for="(column, columnIndex) in row" :key="columnIndex"
        :figura="column"
        @click="cambiaEstadoCasilla(rowIndex, columnIndex)" />
    </div>
    <div class="fila">
      <button @click="reset">Reset</button>
      <button @click="turno = FIGURA.X">{{ FIGURA.X }}</button>
      <button @click="turno = FIGURA.O">{{ FIGURA.O }}</button>
    </div>
  </div>  
</template>

<script setup lang="ts">
import { ref } from "vue";
import CasillaComponent from "./assets/CasillaComponent.vue";

enum FIGURA {
  X = "❌",
  O = "🌀"
}

const turno = ref<FIGURA>(FIGURA.X);

const tablero = ref<string[][]>([
  [ "", "", "" ],
  [ "", "", "" ],
  [ "", "", "" ]
]);

const reset = () => {
  tablero.value = [
    [ "", "", "" ],
    [ "", "", "" ],
    [ "", "", "" ]
  ];
}

const cambiaEstadoCasilla = (fila: number, columna: number) => {
  if (!tablero.value[fila][columna]) {
    tablero.value[fila][columna] = turno.value;
    turno.value = turno.value === FIGURA.X ? FIGURA.O : FIGURA.X;
  }
}
</script>

<style>
html {
  background-color: #1a1a1a;
}

h1 {
  color: white;
}

.contenedor {
  display: flex;
  width: 100%;
  height: 90vh;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.fila {
  width: 350px;
  display: flex;
}
</style>