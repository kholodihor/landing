<script setup lang="ts">
import { ref } from 'vue'
import { Swiper as SwiperClass } from 'swiper/types'
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Navigation } from 'swiper/modules'
import 'swiper/css'
import 'swiper/css/navigation'
import UIButton from '@/components/ui/UIButton.vue'
import AccentedText from '@/components/ui/AccentedText.vue'

interface BotCard {
  id: number
  name: string
  rating: number
  country: string
  age: number
  profession: string
  image: string
  isPremium?: boolean
}

const swiperInstance = ref<SwiperClass | null>(null)

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

const onSwiper = (swiper: SwiperClass) => {
  swiperInstance.value = swiper
}

const bots: BotCard[] = [
  {
    id: 1,
    name: 'Paeonia Castling',
    rating: 1645,
    country: 'HT',
    age: 78,
    profession: 'Herbalist',
    image: '/img/bots/bot1.png',
  },
  {
    id: 2,
    name: 'Cookie',
    rating: 1847,
    country: 'FR',
    age: 32,
    profession: 'Patisserie Chef Apprentice',
    image: '/img/bots/bot2.png',
    isPremium: true,
  },
  {
    id: 3,
    name: 'Olaf Iceberg',
    rating: 773,
    country: 'NO',
    age: 45,
    profession: 'Glaciologist',
    image: '/img/bots/bot3.png',
  },
  {
    id: 4,
    name: 'Ethan Snide',
    rating: 783,
    country: 'CD',
    age: 28,
    profession: 'Obnoxious kid',
    image: '/img/bots/bot4.png',
  },
  {
    id: 5,
    name: 'Hana Biisho',
    rating: 1931,
    country: 'FR',
    age: 36,
    profession: 'Journalist',
    image: '/img/bots/bot5.png',
    isPremium: true,
  },
  {
    id: 6,
    name: '',
    rating: 0,
    country: '',
    age: 0,
    profession: '500+',
    image: '/img/bots/bot_placeholder.png',
    isPremium: false,
  },
]
</script>

<template>
  <section class="bots-section">
    <div class="container">
      <h2 class="section-title">
        From Beginner to Grandmaster,<br />
        <span style="font-weight: 800; color: var(--clr-accent)">with real &nbsp;</span>
        <AccentedText text=" Elo Ratings" color="var(--clr-accent)" />
      </h2>

      <div class="swiper-container">
        <swiper
          :modules="[Navigation]"
          @swiper="onSwiper"
          :slides-per-view="1"
          :space-between="10"
          :loop="true"
          :breakpoints="{
            320: {
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
              slidesPerView: 3.5,
              spaceBetween: 10,
            },
            1024: {
              slidesPerView: 4.5,
              spaceBetween: 10,
            },
            1280: {
              slidesPerView: 6,
              spaceBetween: 10,
            },
            1540: {
              slidesPerView: 6,
              spaceBetween: 10,
            },
          }"
          class="bots-swiper"
        >
          <swiper-slide v-for="bot in bots" :key="bot.id" class="bots-slide">
            <div
              class="bots-card"
              :class="{ 'bots-card--placeholder': bot.name === 'PersonaPlay Bots' }"
            >
              <div class="bots-card-image">
                <img :src="bot.image" :alt="bot.name" />
              </div>
              <div class="bots-card-content">
                <h3 class="bots-card-name">
                  {{ bot.name }}
                  <span v-if="bot.rating > 0" class="rating">({{ bot.rating }})</span>
                  <img
                    v-if="bot.country"
                    :src="`https://flagsapi.com/${bot.country}/flat/24.png`"
                    :alt="bot.country"
                    class="bots-card-flag"
                  />
                </h3>
                <div v-if="bot.country" class="bots-card-info">
                  <span class="details">Age {{ bot.age }} | {{ bot.profession }}</span>
                </div>
                <div v-else class="bots-card-placeholder">
                  <span class="count">{{ bot.profession }}</span>
                  <span class="text">PersonaPlay™ Bots</span>
                </div>
              </div>
            </div>
          </swiper-slide>
        </swiper>
      </div>

      <div class="bots-footer">
        <div class="bots-footer-content">
          <UIButton variant="accent" size="lg" class="explore-btn">Explore All</UIButton>
          <div class="swiper-navigation">
            <button @click="handlePrev" class="nav-button">
              <img src="/svg/chevron.svg" alt="Previous" class="chevron chevron-left" />
            </button>
            <button @click="handleNext" class="nav-button">
              <img src="/svg/chevron.svg" alt="Next" class="chevron chevron-right" />
            </button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.bots-section {
  background-color: var(--clr-bg-lightblue);
  padding: 5rem 0;
  position: relative;
  overflow: hidden;
}

.container {
  max-width: 1440px;
  margin: 0 auto;
  padding: 0 1.5rem;
}

.section-title {
  font-size: 2.5rem;
  font-weight: 700;
  text-align: center;
  margin-bottom: 3rem;
  line-height: 1.2;
}

.swiper-container {
  padding: 1rem 0 2rem;
  position: relative;
}

.bots-footer {
  position: relative;
  margin-top: 2rem;
  display: flex;
  justify-content: center;
}

.bots-footer-content {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1rem;
}

.swiper-navigation {
  display: flex;
  gap: 0.75rem;
}

.nav-button {
  width: 48px;
  height: 48px;
  border-radius: 8px;
  background: white;
  box-shadow: 0px 2px 8px rgba(0, 0, 0, 0.08);
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.2s ease;
  padding: 0;
  margin: 0;
  border: none;
}

.chevron {
  width: 20px;
  height: 20px;
}

.chevron-right {
  transform: rotate(180deg);
}

.nav-button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

.bots-swiper {
  padding: 1rem 0.5rem 3rem;
  width: 100%;
}

.bots-slide {
  width: 205px;
  height: 258px;
  display: flex;
}

.bots-card {
  background: white;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.08);
  display: flex;
  flex-direction: column;
  width: 100%;
  height: 100%;
  min-height: 238px;
  transition:
    transform 0.3s ease,
    box-shadow 0.3s ease;
  position: relative;
}

.bots-card-image {
  position: relative;
  width: 100%;
  overflow: hidden;
}

.bots-card-image img {
  width: 100%;
  object-fit: contain;
  display: block;
}

.bots-card-content {
  padding: 0.5rem 0.75rem 0.75rem;
  flex-grow: 1;
  display: flex;
  flex-direction: column;
  background: white;
}

.bots-card-name {
  font-size: 0.95rem;
  font-weight: 400;
  margin-bottom: 0.25rem;
  line-height: 1.2;
  text-align: left;
  display: flex;
  align-items: center;
  flex-wrap: wrap;
}

.rating {
  font-weight: 600;
  font-size: 0.95em;
  margin-left: 0.25rem;
}

.bots-card-flag {
  width: 18px;
  height: 18px;
  object-fit: cover;
  margin-left: 0.2rem;
}

.bots-card-info {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.75rem;
  margin-top: 0.25rem;
}

.bots-card-placeholder {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  flex-grow: 1;
  gap: 0.5rem;
}

.count {
  font-size: 1rem;
  font-weight: 600;
  line-height: 1;
}

.text {
  font-size: 1rem;
  font-weight: 600;
  text-align: center;
  max-width: 120px;
  line-height: 1.2;
  white-space: nowrap;
}

@media (min-width: 480px) and (max-width: 1279px) {
  .swiper-navigation {
    display: flex;
  }
}

@media (max-width: 479px), (min-width: 1280px) {
  .swiper-navigation {
    display: none;
  }
}

@media (max-width: 768px) {
  .bots-section {
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
