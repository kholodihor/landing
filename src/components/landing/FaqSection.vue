<template>
  <section class="faq-section">
    <div class="container">
      <h2 class="section-title">FAQ</h2>
    </div>

    <div v-for="(item, catIndex) in faqData" :key="catIndex" class="faq-group">
      <h4 style="color: #14A2B8; font-weight: 600">{{ item.category }}</h4>
      <ul class="faq-list">
        <li v-for="(faq, index) in item.faqs" :key="index" class="faq-item" @click="toggleAnswer(catIndex, index)">
          <div class="faq-question">
            <div class="faq-bold">{{ faq.question }}</div>
            <ChevronIcon
              color="#1EA2E4"
              :direction="isOpen(catIndex, index) ? 'top' : 'bottom'"
              class="faq-chevron"
            />
          </div>
          <!-- Answer with transition -->
          <transition name="fade-slide">
            <div
              v-if="isOpen(catIndex, index)"
              class="faq-answer"
            >
              {{ faq.answer }}
            </div>
          </transition>
        </li>
      </ul>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import ChevronIcon from '@/components/ui/ChevronIcon.vue'

interface FaqData {
  category: string;
  faqs: {question: string, answer: string}[];
}

const faqData: FaqData[] = [
  {
    category: 'About Chessiverse',
    faqs:  [
      {
        question: 'What is Chessiverse?',
        answer: 'We use real Elo calculations, simulated across 1+ million calibration games. No inflated ratings—just pure skill-based results.'
      },
      {
        question: 'What makes Chessiverse bots different?',
        answer: 'We use real Elo calculations, simulated across 1+ million calibration games. No inflated ratings—just pure skill-based results.'
      },
      {
        question: 'How is my rating calculated?',
        answer: 'We use real Elo calculations, simulated across 1+ million calibration games. No inflated ratings—just pure skill-based results.'
      },
    ]
  },
  {
    category: 'The Chessiverse Bots',
    faqs:  [
      {
        question: 'Are there different levels of difficulty?',
        answer: 'We use real Elo calculations, simulated across 1+ million calibration games. No inflated ratings—just pure skill-based results.'
      },
      {
        question: 'What makes the bots in Chessiverse unique?',
        answer: 'We use real Elo calculations, simulated across 1+ million calibration games. No inflated ratings—just pure skill-based results.'
      },
      {
        question: 'How accurate are the ratings in Chessiverse?',
        answer: 'We use real Elo calculations, simulated across 1+ million calibration games. No inflated ratings—just pure skill-based results.'
      },
    ]
  },
  {
    category: 'Playing on Chessiverse',
    faqs:  [
      {
        question: 'What types of games can I play?',
        answer: 'We use real Elo calculations, simulated across 1+ million calibration games. No inflated ratings—just pure skill-based results.'
      },
      {
        question: 'Can you tell me more about Challenges?',
        answer: 'We use real Elo calculations, simulated across 1+ million calibration games. No inflated ratings—just pure skill-based results.'
      },
      {
        question: 'Are there any specific ways to practice other than playing games?',
        answer: 'We use real Elo calculations, simulated across 1+ million calibration games. No inflated ratings—just pure skill-based results.'
      },
    ]
  },
  {
    category: 'Other questions',
    faqs:  [
      {
        question: 'What does it cost?',
        answer: 'We use real Elo calculations, simulated across 1+ million calibration games. No inflated ratings—just pure skill-based results.'
      },
      {
        question: 'What if I run into problems?',
        answer: 'We use real Elo calculations, simulated across 1+ million calibration games. No inflated ratings—just pure skill-based results.'
      },
    ]
  },
]

const openFaqs = ref<{ [key: string]: boolean }>({})

function toggleAnswer(catIndex: number, index: number) {
  const key = `${catIndex}-${index}`
  openFaqs.value[key] = !openFaqs.value[key]
}

function isOpen(catIndex: number, index: number) {
  return openFaqs.value[`${catIndex}-${index}`] || false
}
</script>

<style scoped>
/* Section */
.faq-section {
  padding: 5rem 0 0 0;
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

/* FAQ List */
.faq-list {
  width: 50%;
  list-style: none;
  padding: 0;
  margin: 1.5rem auto;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.faq-item {
  gap: 0.75rem;
  background-color: #FFFFFF66;
  backdrop-filter: blur(4px);
  padding: 0.75rem 1.25rem;
  border-radius: 8px;
  font-size: 1.05rem;
  font-weight: 500;
  color: #1a1a1a;
  box-shadow: 0 13.36px 26.72px 0 #14A2B833;
  cursor: pointer;
}

.faq-question {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.faq-chevron {
  min-width: 17px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.faq-bold {
  font-weight: 500;
}

.faq-group {
  margin-bottom: 2rem;
}

.faq-answer {
  margin-top: 0.6rem;
  font-family: var(--font-handwritten);
}

.fade-slide-enter-active,
.fade-slide-leave-active {
  transition: all 0.3s ease;
}

.fade-slide-enter-from,
.fade-slide-leave-to {
  opacity: 0;
  max-height: 0;
  overflow: hidden;
  transform: translateY(-10px);
}

.fade-slide-enter-to,
.fade-slide-leave-from {
  opacity: 1;
  max-height: 500px;
  transform: translateY(0);
}

/* Responsive */
@media (max-width: 1150px) {
  .faq-list {
    width: 60%;
  }
}

@media (max-width: 775px) {
  .faq-list {
    width: 70%;
  }
}

@media (max-width: 600px) {
  .faq-list {
    width: 90%;
  }
}

@media (max-width: 470px) {
  .faq-list {
    width: 95%;
    font-size: 12px !important;
  }

  .faq-bold, .faq-answer {
    font-size: 14px;
  }
}
</style>
