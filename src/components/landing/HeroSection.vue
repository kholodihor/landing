<script setup lang="ts">
import { ref } from 'vue'
import AccentedText from '@/components/ui/AccentedText.vue'
import UIButton from '@/components/ui/UIButton.vue'
import HeroTestimonials from '@/components/landing/HeroTestimonials.vue'

const placeholder = ref<HTMLElement | null>(null)

const handleImageLoaded = () => {
  // Add loaded class to image
  const img = event?.target as HTMLElement
  img?.classList.add('loaded')

  // Hide placeholder
  if (placeholder.value) {
    placeholder.value.style.opacity = '0'
  }
}
</script>

<template>
  <section class="hero">
    <div class="hero-content">
      <div class="hero-text">
        <h1>
          <span>Enjoy <AccentedText text="Stress-Free" /> </span>
          <span class="text-accent">&nbsp;Chess Against</span><br />
          <span class="text-accent">Human-Like Bots</span>
        </h1>
        <p class="hero-text-description">
          Play, practice, and puzzle with over 500 of the world’s most realistic chess bots — no
          pressure, no waiting. Win games, climb the ladder, and grow your rating — all at your own
          pace.
        </p>
        <div class="hero-buttons">
          <UIButton size="lg" icon="/svg/swords.svg" text="Play now for Free!" />
          <div class="start-journey">Start your chess journey</div>
        </div>
      </div>
      <div class="hero-image">
        <div class="image-wrapper">
          <!-- Loading placeholder/skeleton -->
          <div class="image-placeholder" ref="placeholder"></div>
          <!-- SVG with optimized loading -->
          <img
            src="/img/hero/hero_image.svg"
            alt="Chess player"
            loading="lazy"
            width="800"
            height="600"
            class="hero-img"
            @load="handleImageLoaded"
          />
        </div>
      </div>
    </div>
    <HeroTestimonials />
  </section>
</template>

<style scoped>
.hero {
  position: relative;
  width: 100%;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background: url('/img/hero/hero_bg.png') no-repeat center center;
  background-size: cover;
}

.hero-content {
  position: relative;
  z-index: 2;
  display: flex;
  width: 100%;
  justify-content: space-between;
  align-items: center;
  gap: 2rem;
  padding: 2rem var(--container-padding-desktop);
}

.hero-text-description {
  font-size: 1.1rem;
  max-width: 700px;
  font-family: var(--font-handwritten);
}

.hero-text h1 {
  font-size: 2.5rem;
  margin-bottom: 1.5rem;
  line-height: 1.2;
  font-weight: 700;
  text-align: left;
}

.hero-text h1 span {
  font-family: var(--font-heading);
  font-weight: 800;
}

.text-accent {
  color: var(--clr-accent);
}

.hero-buttons {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  margin-top: 2rem;
}

.start-journey {
  font-size: 0.9rem;
  font-weight: 500;
  margin-left: 2rem;
  color: var(--clr-text-grey);
  font-family: var(--font-body);
}

.hero-image {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 50%;
}

.image-wrapper {
  position: relative;
  width: 100%;
  height: 100%;
}

.image-placeholder {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: var(--clr-background-main);
  border-radius: 8px;
  z-index: 1;
}

.hero-img {
  width: 100%;
  height: auto;
  object-fit: contain;
  opacity: 0;
  transition: opacity 0.3s ease-in-out;
  position: relative;
  z-index: 2;
}

.hero-img.loaded {
  opacity: 1;
}

@media (max-width: 1024px) {
  .hero-content {
    flex-direction: column;
    text-align: center;
    padding-top: 2rem;
    align-items: center;
    padding-left: var(--container-padding-tablet);
    padding-right: var(--container-padding-tablet);
  }

  .hero-text {
    max-width: 90%;
    margin-bottom: 2rem;
  }

  .hero-buttons {
    align-items: center;
  }

  .start-journey {
    margin-left: 0;
  }

  .hero-image {
    width: 100%;
    min-width: unset;
    margin: 0 auto;
  }
}

@media (max-width: 768px) {
  .hero-text h1 {
    text-align: center;
  }
  .hero-content {
    padding-left: var(--container-padding-mobile);
    padding-right: var(--container-padding-mobile);
  }
}

@media (max-width: 480px) {
  .hero-text h1 {
    font-size: 1.8rem;
  }

  .hero-text-description {
    font-size: 0.9rem;
  }
}
</style>
