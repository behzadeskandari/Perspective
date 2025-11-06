<script setup>
import { ref, computed } from 'vue'

import Greetings from './components/Greetings.vue'

const perspective = ref(100)
const roatetex = ref(0)
const roatetey = ref(0)
const roatetez = ref(0)
const transformValue = computed(
  () =>
    `perspective(${perspective.value}px) rotateX(${roatetex.value}deg) rotateY(${roatetey.value}deg) rotateZ(${roatetez.value}deg)`,
)

function resetValues(event) {
  event.preventDefault()

  perspective.value = 100
  roatetex.value = 0
  roatetey.value = 0
  roatetez.value = 0
}

function copyTransform(event) {
  const cssText = `transform: ${transformValue.value};`
  navigator.clipboard.writeText(cssText)
  alert('Copied:\n' + cssText)
}
</script>

<template>
  <div id="app">
    <h2>CSS3 Perspective Playground</h2>
    <greetings></greetings>
    <main>
      <section class="settings">
        <div class="settings-container">
          <label>perspective: {{ perspective }}px;</label>
          <input type="range" min="0" max="999" v-model="perspective" />

          <label>rotateX: {{ roatetex }}deg; </label>
          <input type="range" min="-180" max="180" v-model="roatetex" />

          <label>rotateY: {{ roatetey }}deg; </label>
          <input type="range" min="-180" max="180" v-model="roatetey" />

          <label>rotateZ: {{ roatetez }}deg; </label>
          <input type="range" min="-180" max="180" v-model="roatetez" />

          <button type="button" @click="resetValues">Reset</button>
          <button type="button" @click="copyTransform">Copy</button>
        </div>
      </section>
      <section class="output">
        <div class="box-container">
          <div class="box" :style="{ transform: transformValue }"></div>
        </div>
      </section>
    </main>
  </div>

  <h1>You did it!</h1>
  <p>
    Visit <a href="https://vuejs.org/" target="_blank" rel="noopener">vuejs.org</a> to read the
    documentation
  </p>
</template>
