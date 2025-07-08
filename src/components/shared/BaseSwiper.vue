<script setup lang="ts">
import { ref, onBeforeUnmount } from 'vue'
import { Swiper } from 'swiper/vue'
import type { Swiper as SwiperInstance } from 'swiper'
import 'swiper/css'

// Define props
defineProps({
  // Array of Swiper modules (Navigation, Pagination, Autoplay, etc.)
  modules: {
    type: Array,
    default: () => [],
  },
  // Object for all Swiper configuration options
  options: {
    type: Object,
    default: () => ({}),
  },
  // Note: customNavigation and customPagination props removed
  // Navigation methods (handlePrev, handleNext) are still available for parent components
  // Custom container class
  containerClass: {
    type: String,
    default: '',
  },
  // Custom slide class
  slideClass: {
    type: String,
    default: '',
  },
})

// Define emits
const emit = defineEmits(['swiper', 'slideChange', 'reachEnd', 'reachBeginning'])

// Reference to the Swiper instance
const swiperInstance = ref<SwiperInstance | null>(null)

// Handle Swiper initialization
const onSwiper = (swiper: SwiperInstance) => {
  swiperInstance.value = swiper
  emit('swiper', swiper)
}

// Handle slide change
const onSlideChange = () => {
  emit('slideChange', swiperInstance.value)
}

// Handle reach end
const onReachEnd = () => {
  emit('reachEnd', swiperInstance.value)
}

// Handle reach beginning
const onReachBeginning = () => {
  emit('reachBeginning', swiperInstance.value)
}

// Navigation methods - exported for parent components to use
const handlePrev = () => {
  if (swiperInstance.value) {
    swiperInstance.value.slidePrev()
  }
}

const handleNext = () => {
  if (swiperInstance.value) {
    swiperInstance.value.slideNext()
  }
}

// Export navigation methods and Swiper instance for parent components
defineExpose({
  handlePrev,
  handleNext,
  swiperInstance
})

// Clean up on component unmount
onBeforeUnmount(() => {
  if (swiperInstance.value) {
    swiperInstance.value.destroy()
  }
})
</script>

<template>
  <div :class="['base-swiper-container', containerClass]">
    <!-- Swiper component -->
    <swiper
      :modules="modules"
      @swiper="onSwiper"
      @slideChange="onSlideChange"
      @reachEnd="onReachEnd"
      @reachBeginning="onReachBeginning"
      v-bind="options"
      :class="['base-swiper', containerClass]"
    >
      <!-- Default slot for slides -->
      <slot></slot>
    </swiper>

    <!-- Navigation and pagination slots removed, but navigation methods are still available for parent components to use -->
  </div>
</template>

<style scoped>
/* Only keeping essential positioning styles */
.base-swiper-container {
  position: relative;
  width: 100%;
}

.base-swiper {
  width: 100%;
}

/* Navigation container for custom buttons */
.base-swiper-navigation {
  display: flex;
  justify-content: space-between;
  margin-top: 1rem;
}
</style>
