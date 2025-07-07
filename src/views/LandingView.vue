<script setup lang="ts">
import HeroSection from '@/components/landing/HeroSection.vue'
</script>

<template>
  <main>
    <HeroSection />
  </main>
</template>

<style scoped>
main {
  width: 100%;
  min-height: 100vh;
  max-width: var(--container-max-width);
  margin: 0 auto;
  padding: 0 var(--spacing-unit);
}
</style>
