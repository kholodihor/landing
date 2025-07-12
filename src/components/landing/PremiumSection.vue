<template>
  <section class="premium-section">
    <div class="container">
      <div class="premium-content">
        <div class="premium-image">
          <img src="/img/premium/chess.png" alt="Premium Chess Pieces" />
        </div>
        <div class="premium-details">
          <h2 class="premium-title">
            Go Premium—<br />
            Unlock Everything
          </h2>

          <ul class="feature-list">
            <li v-for="(feature, index) in features" :key="index" class="feature-item">
              <ChevronIcon color="var(--clr-golden)" class="premium-chevron" />
              <span class="feature-text">
                <span class="feature-bold">{{ feature.bold }}</span>
                <span class="feature-regular">{{ feature.regular }}</span>
              </span>
            </li>
          </ul>

          <UIButton
            variant="premium"
            class="premium-button"
            icon="/svg/crown.svg"
            text="Get Premium"
          />
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import UIButton from '@/components/ui/UIButton.vue'
import ChevronIcon from '@/components/ui/ChevronIcon.vue'

interface Feature {
  bold: string
  regular: string
}

const features: Feature[] = [
  { bold: '500+ PersonaPlay™ bots', regular: '—every style, every level' },
  { bold: 'Unlimited puzzles', regular: '—sharpen your tactics anytime' },
  { bold: 'Daily & weekly challenges', regular: '—stay sharp' },
  { bold: 'Advanced practice tools', regular: '—train openings, endgames, and more' },
  { bold: 'More surprises inside', regular: "—we're always adding more for Premium users" },
]
</script>

<style scoped>
/* Layout */
.premium-section {
  padding: 2rem var(--container-padding-desktop);
}

.container {
  background: linear-gradient(to bottom, #ffffff, #ffebc5);
  border-top: 15px solid rgba(249, 168, 10, 0.5);
  border-radius: 8px;
  margin: 0 auto;
  padding: 2rem 1.5rem;
}

/* Responsive padding */
@media (max-width: 1024px) {
  .premium-section {
    padding-left: var(--container-padding-tablet);
    padding-right: var(--container-padding-tablet);
  }
}

@media (max-width: 768px) {
  .premium-section {
    padding-left: var(--container-padding-mobile);
    padding-right: var(--container-padding-mobile);
  }
}

.premium-content {
  display: flex;
  align-items: center;
  gap: 4rem;
}

/* Image Section */
.premium-image {
  flex: 1.2;
  display: flex;
  justify-content: center;
  align-items: center;
  padding-right: 2rem;
}

.premium-image img {
  max-width: 100%;
  height: auto;
  transform: scale(1.1);
  transform-origin: bottom left;
}

/* Content Section */
.premium-details {
  flex: 1.8;
  max-width: 700px;
}

/* Typography */
.premium-title {
  font-size: 2.8rem;
  font-weight: 800;
  line-height: 1.1;
  margin-bottom: 2rem;
  display: flex;
  flex-direction: column;
  text-align: left;
}

/* Feature List */
.feature-list {
  list-style: none;
  padding: 0;
  margin: 0 0 2.5rem 0;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.feature-item {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  background: #fff8ec;
  backdrop-filter: blur(4px);
  padding: 0.75rem 1.25rem;
  border-radius: 8px;
  font-size: 1.05rem;
  font-weight: 500;
  color: #1a1a1a;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
}

.feature-text {
  display: inline;
}

.premium-chevron {
  min-width: 17px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.feature-bold {
  font-weight: 600;
}

.feature-regular {
  font-weight: 400;
}

/* Buttons */
.premium-button {
  font-size: 1.1rem;
  font-weight: 600;
  padding: 0.9rem 2rem;
}

/* ===== Responsive Styles ===== */

/* Laptop and below */
@media (max-width: 1280px) {
  .premium-details {
    max-width: 600px;
  }
}

/* Tablet and below */
@media (max-width: 1024px) {
  .premium-section {
    padding-left: var(--container-padding-tablet);
    padding-right: var(--container-padding-tablet);
  }
  
  .premium-content {
    gap: 3rem;
  }

  .premium-title {
    font-size: 2.4rem;
  }

  .premium-image img {
    transform: scale(1);
  }
}

/* Small tablets and below */
@media (max-width: 768px) {
  .premium-section {
    padding-left: var(--container-padding-mobile);
    padding-right: var(--container-padding-mobile);
  }
  
  .premium-content {
    flex-direction: column;
    text-align: center;
    gap: 2rem;
  }

  .premium-image {
    flex: 1;
    max-width: 500px;
    padding-right: 0;
    margin: 0 auto;
  }

  .premium-details {
    flex: 1;
    max-width: 100%;
  }

  .feature-list {
    align-items: center;
  }

  .feature-item {
    width: 100%;
    max-width: 500px;
    text-align: left;
    justify-content: flex-start;
  }

  .premium-button {
    width: auto;
    display: inline-flex;
  }
}

/* Mobile */
@media (max-width: 480px) {
  .container {
    padding: 2rem 1.5rem;
  }
  
  .premium-title {
    font-size: 1.8rem;
    margin-bottom: 1.5rem;
    line-height: 1.2;
  }

  .feature-item {
    font-size: 0.95rem;
    padding: 0.7rem 1rem;
  }

  .premium-button {
    width: 100%;
    justify-content: center;
    font-size: 1rem;
    padding: 0.8rem 1.5rem;
  }
  
  .premium-content {
    gap: 2.5rem;
  }
}
</style>
