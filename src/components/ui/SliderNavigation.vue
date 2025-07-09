<script setup lang="ts">
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
      <img src="/svg/chevron.svg" alt="Previous" class="chevron chevron-left" />
    </button>
    <button 
      @click="onNext" 
      class="nav-button"
      :disabled="nextDisabled"
      aria-label="Next slide"
    >
      <img src="/svg/chevron.svg" alt="Next" class="chevron chevron-right" />
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

.chevron {
  width: 20px;
  height: 20px;
}

.chevron-right {
  transform: rotate(180deg);
}

@media (max-width: 479px), (min-width: 1280px) {
  .slider-navigation {
    display: none;
  }
}
</style>