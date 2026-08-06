<template>
  <li>
    {{ numero1 }} {{ operador }} {{ numero2 }} = {{ resultado }}
  </li>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  numero1: Number,
  numero2: Number,
  operador: String
})

const resultado = computed(() => {
  switch (props.operador) {
    case '+':
      return props.numero1 + props.numero2

    case '-':
      return props.numero1 - props.numero2

    case '*':
      return props.numero1 * props.numero2

    case '/':
      return props.numero2 !== 0
        ? props.numero1 / props.numero2
        : 'Erro'

    default:
      return 'Inválido'
  }
})
</script>