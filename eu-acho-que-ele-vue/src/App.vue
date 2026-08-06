<template>
  <div>
    <h1>Calculadora</h1>

    <input
      type="number"
      v-model.number="numero1"
      placeholder="Primeiro número"
    />

    <input
      type="number"
      v-model.number="numero2"
      placeholder="Segundo número"
    />

    <br><br>

    <button @click="calcular('+')">+</button>
    <button @click="calcular('-')">-</button>
    <button @click="calcular('*')">*</button>
    <button @click="calcular('/')">/</button>

    <hr>

    <h2>Histórico</h2>

    <ul>
      <Conta
        v-for="(conta, index) in historico"
        :key="index"
        :numero1="conta.numero1"
        :numero2="conta.numero2"
        :operador="conta.operador"
      />
    </ul>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Conta from './components/Conta.vue'

const numero1 = ref(0)
const numero2 = ref(0)

const historico = ref([])

function calcular(operador) {
  historico.value.push({
    numero1: numero1.value,
    numero2: numero2.value,
    operador
  })
}
</script>