<template>
  <section class="journey-section">
    <div class="container">
      <div class="bots-images">
        <picture>
          <source media="(max-width: 768px)" srcset="/img/startyourjourney/bots_mobile.png" />
          <img
            src="/img/startyourjourney/bots_desktop.png"
            alt="PersonaPlay Bots"
            class="bots-image"
          />
        </picture>
      </div>
      <div class="journey-card">
        <div class="journey-columns">
          <!-- Column 1: PersonaPlay Bots -->
          <div class="journey-column">
            <div class="column-image">
              <img src="/img/startyourjourney/image_1.png" alt="PersonaPlay Bots" />
            </div>
            <h3 class="column-title">500+ PersonaPlay™<br />Bots</h3>
            <p class="column-subtitle">
              From <span class="bold">fast attackers to stubborn defenders</span>—every bot plays
              with a unique style
            </p>
            <div class="column-link">
              <ChevronIcon color="var(--clr-accent)" class="link-icon" />
              <a href="#" class="link-text">What's <span>PersonaPlay™</span>?</a>
            </div>
          </div>

          <!-- Column 2: Human-like Play -->
          <div class="journey-column">
            <div class="column-image">
              <img src="/img/startyourjourney/image_2.png" alt="Human-like Play" />
            </div>
            <h3 class="column-title">Learn Through Genuine<br />Human-like Play</h3>
            <p class="column-subtitle">
              Master <span class="bold">openings, tactics, endgames, and puzzles</span>—with
              opponents who make human mistakes
            </p>
          </div>

          <!-- Column 3: Track Progress -->
          <div class="journey-column">
            <div class="column-image">
              <img src="/img/startyourjourney/image_3.png" alt="Track Progress" />
            </div>
            <h3 class="column-title">Track Real<br />Progress</h3>
            <p class="column-subtitle">
              Get <span class="bold">bot ratings, game stats, and streaks</span>—see your growth
              over time and breakthrough moments
            </p>
          </div>
        </div>

        <!-- CTA Button -->
        <div class="journey-cta">
          <UIButton variant="accent" size="lg" text="Start your journey now" class="cta-button" />
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import UIButton from '@/components/ui/UIButton.vue'
import ChevronIcon from '@/components/ui/ChevronIcon.vue'
</script>

<style scoped>
/* Layout */
.journey-section {
  padding: 4rem var(--container-padding-desktop);
}

.container {
  max-width: var(--container-max-width, 1440px);
  margin: 0 auto;
  width: 100%;
}

/* Bot Images */
.bots-images {
  display: flex;
  justify-content: center;
  margin-bottom: 2rem;
  width: 100%;
}

.bots-images picture {
  width: 100%;
  display: flex;
  justify-content: center;
}

.bots-image {
  max-width: 100%;
  height: auto;
  display: block;
}

/* Card Layout */
.journey-card {
  background: white;
  border-top: 15px solid var(--clr-accent);
  border-radius: 16px;
  padding: 3rem 3rem 4rem;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
}

/* Columns Layout */
.journey-columns {
  display: flex;
  width: 100%;
  gap: 2rem;
  margin-bottom: 3rem;
}

.journey-column {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

/* Column Content */
.column-image {
  height: 120px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 1.5rem;
}

.column-image img {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
}

.column-title {
  font-size: 1.5rem;
  font-weight: 700;
  margin-bottom: 1rem;
  line-height: 1.3;
  color: #1a1a1a;
}

.column-subtitle {
  font-size: 1rem;
  color: #4a4a4a;
  line-height: 1.5;
  margin-bottom: 1rem;
}

.bold {
  font-weight: 600;
}

/* Link Styling */
.column-link {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  margin-top: auto;
}

.link-text {
  font-weight: 400;
  font-size: 1rem;
}

.link-text span {
  font-weight: 600;
  text-decoration: underline;
}

.link-icon {
  width: 14px;
  height: 14px;
}

/* CTA Button */
.journey-cta {
  position: absolute;
  bottom: -22px;
  left: 50%;
  transform: translateX(-50%);
  z-index: 10;
}

.cta-button {
  min-width: 220px;
}

/* Responsive Styles */
@media (max-width: 1024px) {
  .journey-section {
    padding-left: var(--container-padding-tablet);
    padding-right: var(--container-padding-tablet);
  }

  .journey-card {
    padding: 2.5rem;
  }
}

@media (max-width: 768px) {
  .journey-columns {
    flex-direction: column;
    gap: 3rem;
  }

  .journey-column {
    max-width: 500px;
    margin: 0 auto;
  }

  .column-image {
    height: 100px;
  }
}

@media (max-width: 480px) {
  .journey-section {
    padding-left: var(--container-padding-mobile);
    padding-right: var(--container-padding-mobile);
  }

  .journey-card {
    padding: 2rem 1.5rem;
  }

  .column-title {
    font-size: 1.3rem;
  }

  .column-subtitle {
    font-size: 0.9rem;
  }
}
</style>
