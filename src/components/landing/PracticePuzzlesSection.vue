<template>
  <section class="practice-puzzles-section">
    <div class="container">
      <!-- Practice Section -->
      <div class="section-wrapper practice-wrapper">
        <div class="section-header">
          <h2 class="section-title">
            <img src="/svg/library.svg" alt="Library" class="section-icon" />
            <AccentedText text="Practice" />
          </h2>
        </div>

        <div class="section-content">
          <div class="content-left">
            <div class="info-card">
              <img src="/svg/library.svg" alt="Library" class="card-icon" />
              <div class="info-text">
                <h6>Practice</h6>
                <p>0/601</p>
              </div>
            </div>

            <ul class="menu-list">
              <li v-for="(item, index) in practiceMenuItems" :key="`practice-${index}`">
                <router-link :to="item.link" class="menu-item">
                  <span>{{ item.name }}</span>
                  <img src="/svg/chevron_right.svg" alt="" class="chevron" />
                </router-link>
              </li>
            </ul>
          </div>

          <div class="chessboard-container">
            <p class="chessboard-description">
              <strong>Endgames.</strong> <br />
              (Karpov - Kasparov, 1984.) <br />
              White to play
            </p>
            <img src="/svg/chessboard_1.svg" alt="Chessboard" class="chessboard" />
            <router-link to="/practice">
              <UIButton icon="/svg/swords.svg" text="Practice Now" class="button" />
            </router-link>
          </div>
        </div>
      </div>

      <!-- Puzzles Section -->
      <div class="section-wrapper puzzles-wrapper">
        <div class="section-header">
          <h2 class="section-title">
            <img src="/svg/puzzle.svg" alt="Puzzle" class="section-icon" />
            <AccentedText text="Puzzles" />
          </h2>
        </div>

        <div class="section-content">
          <div class="content-left">
            <div class="info-card">
              <img src="/svg/puzzle.svg" alt="Puzzle" class="card-icon" />
              <div class="info-text">
                <h6>Puzzles</h6>
                <p>0/4320</p>
              </div>
            </div>

            <ul class="menu-list">
              <li v-for="(item, index) in puzzlesMenuItems" :key="`puzzle-${index}`">
                <router-link :to="item.link" class="menu-item">
                  <span>{{ item.name }}</span>
                  <img src="/svg/chevron_right.svg" alt="" class="chevron" />
                </router-link>
              </li>
            </ul>
          </div>

          <div class="chessboard-container">
            <p class="chessboard-description">
              <strong>Novice level.</strong> <br />
              White to play
            </p>
            <img src="/svg/chessboard_2.svg" alt="Chessboard" class="chessboard" />
            <router-link to="/puzzles">
              <UIButton icon="/svg/swords.svg" text="Solve Puzzles" />
            </router-link>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import AccentedText from '@/components/ui/AccentedText.vue'
import UIButton from '@/components/ui/UIButton.vue'

// const practiceMenuItems = ['Openings', 'Middlegames', 'Endgames', 'Masters', 'Custom challenge']
// const puzzlesMenuItems = ['Beginner', 'Novice', 'Intermediate', 'Skilled', 'Advanced']

const practiceMenuItems = [
  { name: 'Openings', link: '/practice/openings' },
  { name: 'Middlegames', link: '/practice/middlegames' },
  { name: 'Endgames', link: '/practice/endgames' },
  { name: 'Masters', link: '/practice/masters' },
  { name: 'Custom challenge', link: '/practice/custom-challenge' },
]

const puzzlesMenuItems = [
  { name: 'Beginner', link: '/puzzles/beginner' },
  { name: 'Novice', link: '/puzzles/novice' },
  { name: 'Intermediate', link: '/puzzles/intermediate' },
  { name: 'Skilled', link: '/puzzles/skilled' },
  { name: 'Advanced', link: '/puzzles/advanced' },
]
</script>

<style scoped>
/* Layout */
.practice-puzzles-section {
  padding: 2rem 0;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
}

.section-wrapper {
  border-radius: 16px;
  padding: 1.5rem;
  margin-bottom: 1.5rem;
}

.section-header {
  width: 100%;
  margin-bottom: 1.5rem;
}

.section-title {
  width: 100%;
  font-size: 2.5rem;
  font-weight: 800;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 0.75rem;
  margin: 0;
  text-align: center;
}

.section-content {
  display: flex;
  flex-direction: column;
  gap: 2rem;
  align-items: center;
}

.content-left {
  order: 2;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  width: 100%;
}

/* Chessboard */
.chessboard-container {
  width: 100%;
  order: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  background: #f8f9fa;
  border-radius: 12px;
  padding: 0;
  margin: 0 auto;
  max-width: 350px;
}

.chessboard {
  width: 100%;
  height: auto;
  object-fit: contain;
}

.chessboard-description {
  text-align: center;
  margin-bottom: 1rem;
  line-height: 1.1;
}

.chessboard-description strong {
  font-weight: 600;
}

/* Info Card */
.info-card {
  border-radius: 12px;
  padding: 1.25rem;
  display: flex;
  justify-content: flex-start;
  gap: 1rem;
  align-items: center;
  box-shadow: 0 4px 12px rgba(20, 162, 184, 0.3);
  width: 100%;
}

.info-text h6 {
  margin: 0 0 0.25rem 0;
  font-size: 1.1rem;
  font-weight: 600;
  color: var(--clr-accent);
}

.info-text p {
  margin: 0;
  font-weight: 600;
  font-size: 0.9rem;
}

.card-icon {
  width: 40px;
  height: 40px;
  opacity: 0.8;
}

/* Menu List */
.menu-list {
  list-style: none;
  padding: 0;
  margin: 0 0 0.5rem 0;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  width: 100%;
}

.menu-item {
  box-shadow: 0 4px 12px rgba(20, 162, 184, 0.3);
  border-radius: 8px;
  padding: 0.75rem 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  cursor: pointer;
  transition: all 0.2s ease;
}

.chevron {
  width: 16px;
  height: 16px;
  opacity: 0.5;
}

/* Buttons */
.button {
  margin-top: 2rem;
  width: 100%;
  max-width: 200px;
}

/* Desktop styles */
@media (min-width: 768px) {
  .practice-puzzles-section {
    padding: 4rem 0;
  }

  .section-wrapper {
    padding: 2rem;
    margin-bottom: 2rem;
  }

  .section-content {
    flex-direction: row;
    align-items: flex-start;
    gap: 4rem;
  }

  .section-header {
    margin-bottom: 2.5rem;
  }

  .practice-wrapper .section-content {
    flex-direction: row-reverse;
  }

  .content-left {
    flex: 1;
    order: unset;
  }

  .chessboard-container {
    flex: 1;
    max-width: 400px;
    order: unset;
  }
}

/* Mobile styles */
@media (max-width: 640px) {
  .section-title {
    font-size: 1.25rem;
  }

  .info-card {
    padding: 1rem;
  }

  .menu-item {
    padding: 0.6rem 0.8rem;
    font-size: 0.9rem;
  }
}
</style>
