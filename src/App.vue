<script setup lang="ts">
import wheelsConfig from './assets/config/wheelsConfig'
import Wheels from './components/wheels/Wheels.vue'
</script>

<template>
  <div class="container">
    <Wheels :config="wheelsConfig" />
  </div>
</template>

<style scoped>
.container {
  display: flex;
  height: 100vh;
  justify-content: center;
  align-items: center;
}
</style>
