<script setup lang="ts">
import UIButton from '@/components/ui/UIButton.vue'
</script>

<template>
  <main>
    <h1>Here will be Landing Page soon...</h1>
    <div class="buttons">
      <UIButton size="sm" icon="/svg/swords.svg" />
      <UIButton size="md" icon="/svg/swords.svg" variant="premium" text="Play" />
    </div>
  </main>
</template>

<style scoped>
main {
  width: 100%;
  max-width: var(--container-max-width);
  margin: 0 auto;
  padding: 0 var(--spacing-unit);
}

h1 {
  margin-top: 2rem;
  font-weight: 400;
}

.buttons {
  display: flex;
  justify-content: center;
  gap: 1rem;
}
</style>
