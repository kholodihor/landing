<script setup lang="ts">
import HeroSection from '@/components/landing/HeroSection.vue'
import BotCardsSection from '@/components/landing/BotCardsSection.vue'
import StylesSection from '@/components/landing/StylesSection.vue'
import ChallengesSection from '@/components/landing/ChallengesSection.vue'
import PracticePuzzlesSection from '@/components/landing/PracticePuzzlesSection.vue'
import PlayYourWaySection from '@/components/landing/PlayYourWaySection.vue'
</script>

<template>
  <main>
    <HeroSection />
    <BotCardsSection />
    <StylesSection />
    <PlayYourWaySection />
    <PracticePuzzlesSection />
    <ChallengesSection />
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
