<template>
  <section class="challenges-section">
    <div class="container">
      <h2 class="section-title">
        <img src="/svg/prize.svg" alt="Trophy" class="section-icon" />
        Challenges
      </h2>

      <div class="swiper-container">
        <BaseSwiper
          :modules="[Navigation]"
          @swiper="onSwiper"
          :options="{
            slidesPerView: 1,
            spaceBetween: 10,
            loop: true,
            breakpoints: {
              320: {
                slidesPerView: 1,
                spaceBetween: 16,
              },
              420: {
                slidesPerView: 1.5,
                spaceBetween: 16,
              },
              480: {
                slidesPerView: 2,
                spaceBetween: 20,
              },
              640: {
                slidesPerView: 2.5,
                spaceBetween: 10,
              },
              768: {
                slidesPerView: 3,
                spaceBetween: 10,
              },
              1024: {
                slidesPerView: 4,
                spaceBetween: 10,
              },
              1280: {
                slidesPerView: 5,
                spaceBetween: 10,
              },
              1540: {
                slidesPerView: 5,
                spaceBetween: 10,
              },
            },
          }"
          containerClass="challenges-swiper"
        >
          <SwiperSlide v-for="challenge in challenges" :key="challenge.id" class="challenges-slide">
            <div class="challenge-card">
              <div class="challenge-card-image">
                <img :src="challenge.image" :alt="challenge.title" />
                <span v-if="challenge.isNew" class="new-badge">New</span>
              </div>
              <div class="challenge-card-content">
                <h3 class="challenge-card-title">{{ challenge.title }}</h3>
                <p class="challenge-card-description">{{ challenge.description }}</p>
              </div>
            </div>
          </SwiperSlide>
        </BaseSwiper>
      </div>

      <div class="challenges-footer">
        <div class="challenges-footer-content">
          <UIButton variant="accent" size="lg" class="explore-btn">Explore All</UIButton>
          <SliderNavigation
            :on-prev="() => swiperInstance?.slidePrev()"
            :on-next="() => swiperInstance?.slideNext()"
            :prev-disabled="false"
            :next-disabled="false"
            class="swiper-navigation"
          />
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { SwiperSlide } from 'swiper/vue'
import { Navigation } from 'swiper/modules'
import BaseSwiper from '@/components/shared/BaseSwiper.vue'
import UIButton from '@/components/ui/UIButton.vue'
import SliderNavigation from '@/components/ui/SliderNavigation.vue'

interface ChallengeCard {
  id: number
  title: string
  description: string
  image: string
  isNew?: boolean
}

const challenges: ChallengeCard[] = [
  {
    id: 1,
    title: 'Chess Club Challenge',
    description:
      'Climb the ranks from friendly games outside the club to a final glorious battle against the resident club superstar. Beware, his playstyle is a bit... unusual.',
    image: '/img/challenges/challenges_1.png',
    isNew: true,
  },
  {
    id: 2,
    title: 'Weekly Challenge',
    description:
      'A rotating event every week with a new theme—could be positional play, time pressure, or weird bot personalities. Sharpen your skills against a different challenge every time.',
    image: '/img/challenges/challenges_2.png',
  },
  {
    id: 3,
    title: 'Daily Endgame Challenge',
    description:
      'One tricky endgame setup per day. You only get one chance—can you play it like a master and convert the win?',
    image: '/img/challenges/challenges_3.png',
  },
  {
    id: 4,
    title: 'Guess the Elo',
    description:
      'Face a lineup of bots matched to your current rating. Each win increases difficulty. How high can you climb before they catch your weakness?',
    image: '/img/challenges/challenges_4.png',
  },
  {
    id: 5,
    title: 'Mystery Match',
    description:
      'You don’t know the bot’s rating, style, or favorite opening. Go in blind and figure them out as the game unfolds. Pure instinct.',
    image: '/img/challenges/challenges_5.png',
  },
]

// Reference to the Swiper instance for navigation controls
const swiperInstance = ref<any | null>(null)

// Get the Swiper instance when it's initialized
const onSwiper = (swiper: any) => {
  swiperInstance.value = swiper
}
</script>

<style scoped>
/* Section */
.challenges-section {
  padding: 5rem 0;
  position: relative;
  overflow: hidden;
}

.container {
  max-width: 1440px;
  margin: 0 auto;
  padding: 0 1.5rem;
}

/* Title */
.section-title {
  font-size: 2.5rem;
  font-weight: 700;
  text-align: center;
  margin-bottom: 3rem;
  line-height: 1.2;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.75rem;
}

.section-icon {
  width: 60px;
  height: 60px;
}

/* Swiper Container */
.swiper-container {
  padding: 1rem 0 2rem;
  position: relative;
}

.challenges-swiper {
  padding: 1rem 0.5rem 3rem;
  width: 100%;
}

/* Challenge Card */
.challenges-slide {
  width: 290px;
  height: 370px;
  display: flex;
}

.challenge-card {
  background: white;
  padding: 1rem;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.08);
  display: flex;
  flex-direction: column;
  width: 100%;
}

.challenge-card-image {
  position: relative;
  width: 100%;
  height: 180px;
  min-height: 180px;
  border-radius: 12px;
  overflow: hidden;
}

.challenge-card-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

.new-badge {
  position: absolute;
  top: 12px;
  left: 12px;
  background: var(--clr-accent);
  color: white;
  font-size: 0.75rem;
  font-weight: 600;
  padding: 0.25rem 0.75rem;
  border-radius: 12px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.challenge-card-content {
  /* padding: 1.25rem; */
  flex-grow: 1;
  display: flex;
  flex-direction: column;
}

.challenge-card-title {
  font-size: 1rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
  line-height: 1.3;
  color: var(--clr-text);
  text-align: left;
}

.challenge-card-description {
  color: var(--clr-text-secondary);
  font-size: 14px;
  line-height: 1.4;
  margin: 0;
}

/* Footer */
.challenges-footer {
  position: relative;
  margin-top: 2rem;
  display: flex;
  justify-content: center;
}

.challenges-footer-content {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1rem;
}

/* Navigation */
.swiper-navigation {
  display: flex;
  gap: 0.75rem;
}

/* Responsive */
@media (min-width: 350px) {
  .swiper-navigation {
    display: flex;
  }
}

@media (min-width: 1280px) {
  .swiper-navigation {
    display: none;
  }
}

@media (max-width: 768px) {
  .challenges-section {
    padding: 3rem 0;
  }

  .section-title {
    font-size: 2rem;
    margin-bottom: 2rem;
  }
}

@media (max-width: 480px) {
  .section-title {
    font-size: 1.75rem;
  }
}
</style>
