<script setup lang="ts">
import ChevronIcon from './ChevronIcon.vue'

interface Props {
  onPrev: () => void
  onNext: () => void
  prevDisabled?: boolean
  nextDisabled?: boolean
  class?: string
}

defineProps<Props>()
</script>

<template>
  <div class="slider-navigation" :class="$attrs.class">
    <button 
      @click="onPrev" 
      class="nav-button"
      :disabled="prevDisabled"
      aria-label="Previous slide"
    >
      <ChevronIcon direction="left" color="var(--clr-accent)" />
    </button>
    <button 
      @click="onNext" 
      class="nav-button"
      :disabled="nextDisabled"
      aria-label="Next slide"
    >
      <ChevronIcon direction="right" color="var(--clr-accent)" />
    </button>
  </div>
</template>

<style scoped>
.slider-navigation {
  display: flex;
  gap: 0.75rem;
}

.nav-button {
  width: 42px;
  height: 42px;
  border-radius: 8px;
  background: white;
  box-shadow: 0px 2px 8px rgba(20, 162, 184, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.2s ease;
  padding: 0;
  margin: 0;
  border: none;
}

.nav-button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

.chevron-icon {
  width: 16px;
  height: 16px;
  transition: transform 0.2s ease;
}

.nav-button:hover:not(:disabled) .chevron-icon {
  transform: translateX(var(--hover-translate, 2px));
}

.nav-button:hover:not(:disabled) .chevron-icon[direction="right"] {
  --hover-translate: -2px;
}

@media (max-width: 479px), (min-width: 1280px) {
  .slider-navigation {
    display: none;
  }
}
</style>