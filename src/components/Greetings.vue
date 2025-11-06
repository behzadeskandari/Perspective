<template>
  <div :style="colorStyle">{{ count }} ++</div>
  <p style="color: white">{{ changeClickValue }}</p>
  <button @click="clickEvent" style="color: white; background: black">click</button>
</template>

<script setup>
import { ref, computed } from 'vue'

const count = ref(0)

const colorStyle = computed(() => ({
  color: count.value % 2 === 0 ? 'red' : 'blue',
  fontSize: '24px',
}))

const changeClickValue = computed(() => `You clicked ${count.value} times`)

function clickEvent() {
  count.value++
  console.log('Button clicked, count:', count.value)
}
</script>

<style scoped>
button {
  padding: 8px 16px;
  margin-top: 12px;
  cursor: pointer;
}
</style>
