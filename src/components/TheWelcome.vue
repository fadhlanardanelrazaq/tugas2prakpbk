<template>
  <div class="container" :style="{ backgroundColor: bgColor }">
    <h1>{{ heading }}</h1>
    <div class="input-container">
      <input type="text" v-model="inputText" :class="{ 'input-red': isRed }" @input="handleInput">
      <label for="input-text">ketik 1 background akan berwarna pink, jika ketik yang lain akan berwarna ungu</label>
    </div>
    <p :style="{ color: textColor }" class="text">{{ inputText }}</p>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const inputText = ref('')
const isRed = ref(false)
const textColor = ref('black')
const heading = 'Ubah Warna Background'
const bgColor = ref('black')

const handleInput = () => {
  if (inputText.value.toLowerCase() === '1') {
    isRed.value = true
    bgColor.value = '#ffcccc'
  } else {
    isRed.value = false
    bgColor.value = 'purple'
  }
}
</script>

<style scoped>
.container {
  text-align: center;
  margin-top: 50px;
  transition: background-color 0.3s ease-in-out;
}

.input-container {
  margin-top: 20px;
}

.input-red {
  border-color: red;
}

label {
  display: block;
  margin-top: 10px;
  font-size: 18px;
}

.text {
  transition: color 0.3s ease-in-out;
}
</style>

