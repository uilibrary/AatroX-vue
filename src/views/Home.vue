<template>
  <h5>{{ counter }} x 2 = {{ times2 }}</h5>
  <button @click="inc">Increment</button>
</template>

<script setup>
import { useState, useGetters, useMutations } from '../store/helper'

  const { counter } = useState(['counter'])
  const { times2 } = useGetters(['times2'])
  const { setCounter } = useMutations(['setCounter'])
  const inc = () => setCounter(counter.value + 1)

  return { inc, counter, times2, setCounter }

  

</script>

<style lang="scss" scoped>
  $primary: #A12568;
  .text-primary {
    color: $primary;
  }
</style>