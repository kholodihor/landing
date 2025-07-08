<script setup lang="ts">
defineProps<{
  text: string
  color?: string
}>()
</script>

<template>
  <span class="accented-text" :style="{ color: color || 'inherit' }">
    {{ text }}
    <img src="/svg/under_line.svg" alt="" class="underline" aria-hidden="true" />
  </span>
</template>

<style scoped>
.accented-text {
  color: inherit;
  font-family: inherit;
  font-weight: inherit;
  position: relative;
  display: inline-block;
}

.underline {
  position: absolute;
  bottom: -4px;
  left: 0;
  width: 100%;
  height: auto;
  display: block;
}
</style>
