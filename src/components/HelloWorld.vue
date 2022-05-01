<script setup>
import { ref } from 'vue'
import { NButton } from 'naive-ui'
import { NA, NH1, NP, NCode } from 'naive-ui'

defineProps({
  msg: String
})

const count = ref(0)
</script>

<template>
  <n-h1>{{ msg }}</n-h1>

  <n-p>
    Recommended IDE setup:
    <n-a href="https://code.visualstudio.com/" target="_blank">VS Code</n-a>
    +
    <n-a href="https://github.com/johnsoncodehk/volar" target="_blank">Volar</n-a>
  </n-p>

  <n-p>
    <n-a href="https://vitejs.dev/guide/features.html" target="_blank">
      Vite Documentation
    </n-a>
    |
    <n-a href="https://v3.vuejs.org/" target="_blank">Vue 3 Documentation</n-a>
  </n-p>

  <n-button type="default" @click="count++">count is: {{ count }}</n-button>
  <n-p>
    Edit
    <n-code>components/HelloWorld.vue</n-code> to test hot module replacement.
  </n-p>
  <div class="container border bg-alert">
    <n-button type="primary" class="btn btn-primary">Button</n-button>
    
  </div>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>

<script>
</script>