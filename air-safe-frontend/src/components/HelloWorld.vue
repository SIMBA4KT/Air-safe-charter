<script setup>
import { ref } from 'vue'

const count = ref(0)
</script>

<template>
  <div class="hello-world">
    <h1>Hello World!</h1>
    <p>Count is: {{ count }}</p>
    <button @click="count++">Increment</button>
  </div>
</template>
