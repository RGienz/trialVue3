<script setup lang="ts">
import AngelaFirst from './components/AngelaFirst.vue'
</script>

<template>
  <header>
    <div class="wrapper">
      <!-- Include the AngelaFirst component here -->
      <AngelaFirst />
    </div>
  </header>
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }
}
</style>
