<script setup lang="ts">
import { computed } from 'vue';

type Direction = 'right' | 'left' | 'top' | 'bottom';

interface Props {
  color?: string;
  direction?: Direction;
}

const props = withDefaults(defineProps<Props>(), {
  color: 'currentColor',
  direction: 'right',
});

const rotationDegrees = computed(() => {
  switch (props.direction) {
    case 'top': return -90;
    case 'right': return 0;
    case 'bottom': return 90;
    case 'left': return 180;
    default: return 0;
  }
});
</script>

<template>
  <svg 
    :style="{ transform: `rotate(${rotationDegrees}deg)` }"
    width="9" 
    height="17" 
    viewBox="0 0 9 17" 
    fill="none" 
    xmlns="http://www.w3.org/2000/svg"
  >
    <path
      d="M-4.11284e-08 1.44091C-1.84283e-08 0.92159 0.444429 0.5 0.99188 0.5L8.7093 7.83447C8.90297 8.01818 9 8.25909 9 8.5L-3.49691e-07 8.5L-4.11284e-08 1.44091Z"
      :fill="color"
    />
    <path
      d="M0.99188 16.5C0.444429 16.5 -3.31263e-07 16.0784 -3.08563e-07 15.5591L0 8.5L9 8.5C9 8.74091 8.90297 8.98182 8.7093 9.16553L0.99188 16.5Z"
      :fill="color"
      fill-opacity="0.8"
    />
    <defs>
      <linearGradient
        id="paint0_linear_1682_37722"
        x1="9.22842"
        y1="4.5"
        x2="3.69497"
        y2="4.5"
        gradientUnits="userSpaceOnUse"
      >
        <stop stop-color="#32BDEF" />
        <stop offset="1" stop-color="#1EA2E4" />
      </linearGradient>
      <linearGradient
        id="paint1_linear_1682_37722"
        x1="9.22842"
        y1="12.5"
        x2="3.69497"
        y2="12.5"
        gradientUnits="userSpaceOnUse"
      >
        <stop offset="0.365" stop-color="#199AE0" />
        <stop offset="0.699" stop-color="#1898DE" />
        <stop offset="0.819" stop-color="#1691D8" />
        <stop offset="0.905" stop-color="#1186CC" />
        <stop offset="0.974" stop-color="#0A75BC" />
        <stop offset="1" stop-color="#076CB3" />
      </linearGradient>
    </defs>
  </svg>
</template>
