<script setup lang="ts">
import { computed, withDefaults } from 'vue'

type ButtonVariant = 'accent' | 'dark' | 'premium' | 'outlined'

type ButtonSize = 'default' | 'sm' | 'lg' | 'icon'

interface ButtonProps {
  as?: string | object
  variant?: ButtonVariant
  size?: ButtonSize
  icon?: string
  text?: string
  disabled?: boolean
  class?: string
}

const props = withDefaults(defineProps<ButtonProps>(), {
  as: 'button',
  variant: 'accent',
  size: 'default',
  disabled: false,
  class: '',
})

const buttonClasses = computed(() => [
  'button',
  `button--${props.variant}`,
  `button--${props.size}`,
  { 'button--disabled': props.disabled },
  props.class,
])
</script>

<template>
  <component :is="as" :class="buttonClasses" :disabled="disabled">
    <slot name="icon">
      <component v-if="icon" :is="icon" />
    </slot>
    <template v-if="size !== 'sm'">
      <span v-if="$slots.default">
        <slot />
      </span>
      <span v-else-if="text">
        {{ text }}
      </span>
    </template>
  </component>
</template>

<style scoped>
/* Base Styles */
.button {
  /* Layout */
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 1rem;
  min-width: 220px;
  padding: 0.7rem 2.8rem;
  font-size: 1rem;
  white-space: nowrap;

  /* Visual */
  border: 1px solid transparent;
  border-radius: 6px;
  cursor: pointer;
  transition: all 0.2s ease-in-out;
  outline: none;
}

/* Button Text and Icons */
.button,
.button * {
  font-family: 'Clash Display', sans-serif;
  font-weight: 600;
}

.button svg {
  width: 1rem;
  height: 1rem;
  flex-shrink: 0;
  pointer-events: none;
}

/* States */
.button:disabled {
  pointer-events: none;
  opacity: 0.5;
}

/* Variants */
.button--accent {
  background: linear-gradient(to bottom, #14a2b8, #40bfd3);
  color: white;
}

.button--dark {
  background: linear-gradient(to bottom, #676767, #4b4b4b);
  color: white;
}

.button--premium {
  background: linear-gradient(to bottom, #ffdfa2, #f9a80a, #ffb82e);
  color: #333;
}

.button--outlined {
  background: #ffffff;
  border: 1px solid #faac14;
  color: #333;
}

/* Hover States */
.button--accent:hover,
.button--dark:hover,
.button--premium:hover {
  opacity: 0.95;
}

.button--outlined:hover {
  background-color: #fffbf5;
}

/* Sizes */
.button--sm {
  min-width: 3rem;
  width: 3rem;
  height: 3rem;
  padding: 0;
  border-radius: 50%;
}

.button--lg {
  height: 2.75rem;
  padding: 0 2rem;
}

.button--icon {
  min-width: auto;
  width: 2.5rem;
  height: 2.5rem;
  padding: 0;
}

/* Responsive */
@media (max-width: 768px) {
  .button {
    min-width: 170px;
  }
}
</style>
