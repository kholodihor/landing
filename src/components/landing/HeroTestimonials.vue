<template>
  <section class="testimonials">
    <div class="testimonials-container">
      <BaseSwiper
        :modules="[Autoplay]"
        :options="{
          slidesPerView: 1,
          spaceBetween: 30,
          autoplay: {
            delay: 3000,
            disableOnInteraction: false,
            pauseOnMouseEnter: true,
          },
          loop: true,
          speed: 1500,
          pagination: {
            clickable: true,
          },
          breakpoints: {
            640: {
              slidesPerView: 1,
              spaceBetween: 20,
            },
            768: {
              slidesPerView: 2,
              spaceBetween: 30,
            },
            1024: {
              slidesPerView: 3.5,
              spaceBetween: 40,
            },
            1540: {
              slidesPerView: 4.5,
              spaceBetween: 40,
            },
          },
        }"
        containerClass="testimonials-swiper"
      >
        <SwiperSlide
          v-for="testimonial in testimonials"
          :key="testimonial.id"
          class="testimonial-slide"
        >
          <div class="testimonial-card">
            <div class="testimonial-quote">
              <IconQuotes color="var(--clr-accent)" />
            </div>
            <p class="testimonial-text">{{ testimonial.text }}</p>
            <div class="testimonial-author">
              <img src="/svg/chessiverse_avatar.svg" alt="" />
              {{ testimonial.name }}
            </div>
          </div>
        </SwiperSlide>
      </BaseSwiper>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { SwiperSlide } from 'swiper/vue'
import { Autoplay } from 'swiper/modules'
import IconQuotes from '@/components/icons/IconQuotes.vue'
import BaseSwiper from '@/components/shared/BaseSwiper.vue'

interface Testimonial {
  id: number
  name: string
  text: string
}

const testimonials = ref<Testimonial[]>([
  {
    id: 1,
    name: 'Jacob N.',
    text: 'I love how easy it is to pick my level and jump into a game. The bots play like real people, which makes practice actually fun. It’s a great way to get into chess at my own pace.',
  },
  {
    id: 2,
    name: 'Emily R.',
    text: "Sometimes I just want to make a wild blunder and see what happens—no pressure, no trash talk. Just me and a cowboy bot named Tim Grant trying to outplay each other. It's the most fun I’ve ever had with chess.",
  },
  {
    id: 3,
    name: 'Devika S.',
    text: "The missions feel much more human than playing a perfect engine. There’s no robotic perfection—just opponents with real quirks and styles. It actually feels like you're learning how to beat real players.",
  },
  {
    id: 4,
    name: 'Tomas L.',
    text: 'The daily challenges keep me coming back, and the bots are perfect for practicing openings during my lunch break. I genuinely feel like part of a community.',
  },
  {
    id: 5,
    name: 'Layla M.',
    text: 'The variety of bot personalities is amazing. Some play aggressive, some slow and sneaky—it’s never boring. It’s helped me prepare for real opponents without the stress.',
  },
  {
    id: 6,
    name: 'Carlos G.',
    text: 'I’ve improved so much without even realizing it. At first, I just wanted a casual way to play, but these bots really challenge you if you let them. Super addictive.',
  },
  {
    id: 7,
    name: 'Sophie K.',
    text: 'I used to be nervous playing online, but the bots gave me a safe space to grow my confidence. Now I’m taking on real players—and winning more often than not!',
  },
])
</script>

<style scoped>
.testimonials {
  width: 100%;
  padding: 4rem 0;
  display: none; /* Hide by default */
}

/* Show only on desktop (1024px and up) */
@media (min-width: 1024px) {
  .testimonials {
    display: block;
  }
}

.testimonials-container {
  /* max-width: 1400px; */
  margin: 0 auto;
}

.testimonials-swiper {
  width: 100%;
  padding-bottom: 3rem;
  display: flex;
  justify-content: center;
  align-items: center;
}

.testimonial-slide {
  min-width: 378px;
  height: auto;
  display: flex;
}

.testimonial-card {
  background-color: #ffffff;
  border-radius: 12px;
  padding: 1.5rem;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.05);
  height: 100%;
  display: flex;
  flex-direction: column;
  position: relative;
  /* border-top: 4px solid var(--clr-accent); */
}

.testimonial-quote {
  margin-bottom: 1rem;
}

.testimonial-text {
  font-size: 1rem;
  line-height: 1.6;
  margin-bottom: 1.5rem;
  flex-grow: 1;
}

.testimonial-author {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  gap: 0.5rem;
  padding: 0 1rem;
  font-weight: 500;
  font-size: 0.9rem;
  margin-top: auto;
}

@media (max-width: 1024px) {
  .testimonials {
    padding-left: var(--container-padding-tablet);
    padding-right: var(--container-padding-tablet);
  }
}

@media (max-width: 768px) {
  .testimonials {
    padding-left: var(--container-padding-mobile);
    padding-right: var(--container-padding-mobile);
  }
}
</style>
