<template>
  <section class="courses-section">
    <div class="container">
      <h2 class="section-title">
        <img src="/svg/hand_with_book.svg" alt="Trophy" class="section-icon" />
        Courses
      </h2>

      <div class="swiper-container">
        <BaseSwiper
          :modules="[Navigation]"
          @swiper="onSwiper"
          :options="{
            slidesPerView: 1,
            spaceBetween: 0,
            loop: true
          }"
          containerClass="courses-swiper"
        >
          <SwiperSlide v-for="course in courses" :key="course.id" class="courses-slide">
            <div v-if="course.released" class="courses-card">
              <div class="courses-card-image">
                <img :src="course.image" :alt="course.title" />
                <span v-if="course.isNew" class="new-badge">New</span>
              </div>
              <div class="courses-card-content">
                <div class="courses-card-author">
                  Author: <div style="font-weight: 600"> {{ course.author }}</div>
                </div>
                <h3 class="courses-card-title">{{ course.title }}</h3>
                <p class="courses-card-description">{{ course.description }}</p>
                <div class="courses-card-buttons">
                  <UIButton variant="accent" class="course-btn">Join the waitlist</UIButton>
                  <UIButton variant="outlined-blue" class="course-btn">Read More</UIButton>
                </div>

                <div class="rating-stars">
                  <span
                    v-for="n in 5"
                    :key="n"
                    class="star"
                    :class="{ full: n <= course.rating }"
                  >
                    ★
                  </span>
                </div>
              </div>
            </div>
            <div v-else class="courses-card">
              <div class="courses-card-image" style="background-color: #ECE1E133; max-width: 300px">
                <span class="new-badge" style="background-color: #9E9E9E">Coming soon</span>
              </div>
              <div class="courses-card-content" style="display: flex; justify-content: center; margin-left: 1rem">
                <h3 class="courses-card-title">Coming soon...</h3>
              </div>
            </div>
          </SwiperSlide>
        </BaseSwiper>
      </div>

      <div class="courses-footer">
        <div class="courses-footer-content">
          <UIButton variant="accent" size="lg" class="explore-btn">All Courses</UIButton>
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

interface CourseCard {
  id: number,
  author: string,
  title: string
  description: string
  image: string
  isNew?: boolean,
  released: boolean
}

const courses: CourseCard[] = [
  {
    id: 1,
    author: 'IM John Bartholomew',
    title: 'Qa5 Scandi course',
    description:
      'The Scandinavian Defense has been a mainstay of my chess opening repertoire for over 20 years. I’ve always felt that this opening provid ...',
    image: '/img/courses/author.png',
    isNew: true,
    rating: 5,
    released: true
  },
  {
    id: 2,
    author: 'IM John Bartholomew',
    title: 'Qa5 Scandi course',
    description:
      'The Scandinavian Defense has been a mainstay of my chess opening repertoire for over 20 years. I’ve always felt that this opening provid ...',
    image: '/img/courses/author.png',
    isNew: true,
    rating: 5,
    released: false
  }
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
.courses-section {
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
  margin-bottom: 1rem;
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

.courses-swiper {
  padding: 1rem 0.5rem 3rem;
  width: 100%;
}

/* Course Card */
.courses-slide {
  height: 350px;
  display: flex;
}

.courses-card {
  width: 62%;
  margin: 0 auto;
  background: white;
  padding: 1rem;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.08);
  display: flex;
  flex-direction: row;
  height: 100%;
}

.courses-card-image {
  position: relative;
  width: 100%;
  border-radius: 12px;
  overflow: hidden;
}

.courses-card-image img {
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

.courses-card-content {
  padding: 1.25rem;
  flex-grow: 1;
  display: flex;
  flex-direction: column;
}

.courses-card-author {
  display: flex;
  gap:0.3rem;
  font-size: 11px;
  margin-bottom: 1.5rem
}


.courses-card-title {
  font-size: 1rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
  line-height: 1.3;
  color: var(--clr-text);
  text-align: left;
}

.courses-card-description {
  color: var(--clr-text-secondary);
  font-size: 14px;
  line-height: 1.4;
  margin: 0;
}

.courses-card-buttons {
  margin-top: 2rem;
  display: flex;
  gap: 1.5rem;

  .course-btn{
    width: 170px;
  }
}

.rating-stars {
  margin-top: 2rem;
  background: white;
  padding: 0 1rem;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.08);
  display: flex;
  gap: 0.1rem;
  font-size: 1.5rem;
  color: #ccc; /* default gray */
  width: fit-content;
}

.star.full {
  color: gold; /* filled yellow stars */
}

/* Footer */
.courses-footer {
  position: relative;
  margin-top: 2rem;
  display: flex;
  justify-content: center;
}

.courses-footer-content {
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
@media (max-width: 1280px) {
  .courses-card {
    width: 70%;
  }
}

@media (max-width: 1140px) {
  .courses-card {
    width: 80%;
  }
}

@media (max-width: 995px) {
  .courses-card {
    width: 90%;
  }
}

@media (max-width: 905px) {
  .courses-card {
    width: 100%;
  }
}

@media (max-width: 815px) {
  .courses-slide {
    height: 650px;
  }

  .courses-card {
    width: 70%;
    margin: 0 auto;
    flex-direction: column;
    align-items: center;
  }

  .courses-card-image {
    height: 180px;
    min-height: 300px;
    display: flex;
    justify-content: center;
  }
}

@media (max-width: 640px) {
  .courses-card {
    width: 90%;
    padding: 0.5rem;
  }
}

@media (max-width: 520px) {
  .container {
    padding: 0 0.1rem;
  }

  .courses-slide {
    height: 691px;
  }

  .courses-card {
    width: 100%;
  }

  .courses-card-buttons{
    flex-direction: column;
    gap: 0.5rem;
    align-items: center;
  }

  .courses-card-content{
    align-items: center;
  }
}
</style>
