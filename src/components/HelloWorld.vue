<script setup>
import { ref } from 'vue'


// defineProps({
//   msg: String,
// })


//const count = ref(0)
const modelCelsius = defineModel("c", {default : 0})
const modelFahrenheit = defineModel("f", {default : 32})
const modelKelvin = defineModel("k", {default : 273.15})

const updateTemp = (unit, e) => {
  switch (unit) {
    case 'c':
      modelKelvin.value = (e.target.value-0)+273.15
      modelFahrenheit.value = (e.target.value-0)*9/5+32
    break;
    case 'f':
      modelKelvin.value = (e.target.value-0)*5/9-305.15
      modelCelsius.value = (e.target.value-0)*5/9-32
    break;
    case 'k':
      modelCelsius.value = (e.target.value-0)-273.15
      modelFahrenheit.value = (e.target.value-0)*9/5+241.15
    break;
  }
}
</script>

<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <p>Celsius</p>
    <input type="number" v-model="modelCelsius" @input="e => {updateTemp('c', e)}"></input>
    <p>Fahrenheit</p>
    <input type="number" v-model="modelFahrenheit" @input="e => {updateTemp('f', e)}"></input>
    <p>Kelvin</p>
    <input type="number" v-model="modelKelvin" @input="e => {updateTemp('k', e)}"></input>
  </div>

  <!-- <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Install
    <a href="https://github.com/vuejs/language-tools" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p> -->
</template>

<!-- <style scoped>
.read-the-docs {
  color: #888;
}
</style> -->
