<script setup lang="ts">
import HeroSection from '@/components/landing/HeroSection.vue'
import BotCardsSection from '@/components/landing/BotCardsSection.vue'
import StylesSection from '@/components/landing/StylesSection.vue'
import ChallengesSection from '@/components/landing/ChallengesSection.vue'
import PracticePuzzlesSection from '@/components/landing/PracticePuzzlesSection.vue'
import PlayYourWaySection from '@/components/landing/PlayYourWaySection.vue'
import PremiumSection from '@/components/landing/PremiumSection.vue'
import StartYourJourney from '@/components/landing/StartYourJourney.vue'
import Footer from '@/components/landing/Footer.vue'
</script>

<template>
  <main>
    <HeroSection />
    <BotCardsSection />
    <StylesSection />
    <PlayYourWaySection />
    <PracticePuzzlesSection />
    <ChallengesSection />
    <PremiumSection />
    <StartYourJourney />
    <Footer />
  </main>
</template>

<style scoped>
main {
  width: 100%;
  min-height: 100vh;
  margin: 0 auto;
}
</style>
