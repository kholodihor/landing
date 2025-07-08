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
    text: "I love how simple it was to choose my level and start a match right away. The bots actually feel like real people, which makes practicing so much more fun. It's a fun way to get into chess at my own pace.",
  },
  {
    id: 2,
    name: 'Emily R.',
    text: "I've played games in which I go ahead and want to make a bad fun blunder, no trash talk, just me and a weird cowboy bot named Tim Grant trying to outdo each other. I've never played chess this much. The bots are hilarious and aren't just the right balance.",
  },
  {
    id: 3,
    name: 'Devika S.',
    text: 'The online training has missions which feels way more realistic than playing a perfect engine. No robot-like confidence removing just perform exactly against different styles. The fact they play like people makes them so enjoyable.',
  },
  {
    id: 4,
    name: 'Tomas L.',
    text: "The daily challenges keep me motivated and the bots give me a chance to practice my openings during breaks. I've become part of the community.",
  },
  {
    id: 5,
    name: 'Tomas L.',
    text: "The daily challenges keep me motivated and the bots give me a chance to practice my openings during breaks. I've become part of the community.",
  },
])
</script>

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
