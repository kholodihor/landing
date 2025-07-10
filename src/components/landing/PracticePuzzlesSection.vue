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
              <li
                v-for="(item, index) in practiceMenuItems"
                :key="`practice-${index}`"
                class="menu-item"
              >
                <span>{{ item }}</span>
                <img src="/svg/chevron_right.svg" alt="" class="chevron" />
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

            <UIButton icon="/svg/swords.svg" text="Practice Now" class="button" />
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
              <li
                v-for="(item, index) in puzzlesMenuItems"
                :key="`puzzle-${index}`"
                class="menu-item"
              >
                <span>{{ item }}</span>
                <img src="/svg/chevron_right.svg" alt="" class="chevron" />
              </li>
            </ul>
          </div>

          <div class="chessboard-container">
            <p class="chessboard-description">
              <strong>Novice level.</strong> <br />
              White to play
            </p>
            <img src="/svg/chessboard_2.svg" alt="Chessboard" class="chessboard" />
            <UIButton icon="/svg/swords.svg" text="Solve Puzzles" />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import AccentedText from '@/components/ui/AccentedText.vue'
import UIButton from '@/components/ui/UIButton.vue'

const practiceMenuItems = ['Openings', 'Middlegames', 'Endgames', 'Masters', 'Custom challenge']
const puzzlesMenuItems = ['Beginner', 'Novice', 'Intermediate', 'Skilled', 'Advanced']
</script>

<style scoped>
.practice-puzzles-section {
  padding: 2rem 0;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
}

.button {
  margin-top: 2rem;
}
.section-wrapper {
  border-radius: 16px;
  padding: 1.5rem;
  margin-bottom: 1.5rem;
  overflow: hidden;
}

.section-header {
  width: 100%;
  margin-bottom: 2.5rem;
}

.section-title {
  width: 100%;
  font-size: 2rem;
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
}

.content-left {
  order: 2;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.chessboard-container {
  order: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  background: #f8f9fa;
  border-radius: 12px;
  padding: 1rem;
  margin: 0 auto;
  max-width: 300px;
  width: 100%;
}

.chessboard {
  width: 100%;
  height: auto;
  object-fit: contain;
}

.chessboard-description {
  text-align: center;
  margin-bottom: 1rem;
  line-height: 1.5;
}

.chessboard-description strong {
  font-weight: 600;
}

/* Desktop styles */
@media (min-width: 1024px) {
  .practice-puzzles-section {
    padding: 4rem 0;
  }

  .section-wrapper {
    padding: 2rem;
    margin-bottom: 2rem;
  }

  .section-content {
    flex-direction: row;
    align-items: center;
    gap: 4rem;
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

.info-card {
  border-radius: 12px;
  padding: 1.25rem;
  display: flex;
  justify-content: flex-start;
  gap: 1rem;
  align-items: center;
  box-shadow: 0 4px 12px rgba(20, 162, 184, 0.3);
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

.menu-list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  margin-bottom: 0.5rem;
}

.button-container {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 1.5rem;
  padding: 0;
  width: 100%;
  background: pink;
}

/* Align button under chessboard */
.practice-wrapper .button-container {
  justify-content: center;
  padding-left: 0;
  padding-right: 50%; /* Push to align under chessboard */
}

.puzzles-wrapper .button-container {
  justify-content: center;
  padding-right: 0;
  padding-left: 50%; /* Push to align under chessboard */
}

/* Ensure buttons are properly sized */
.button-container :deep(.button) {
  width: 200px; /* Match chessboard width */
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

/* .menu-item:hover {
  border-color: #adb5bd;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
} */

.chevron {
  width: 16px;
  height: 16px;
  opacity: 0.5;
}

.chessboard-container {
  display: flex;
  justify-content: center;
  align-items: center;
  background: #f8f9fa;
  border-radius: 12px;
  overflow: hidden;
  padding: 1rem;
  align-self: start;
}

.chessboard {
  max-width: 100%;
  height: auto;
  object-fit: contain;
}

/* Responsive Design */
@media (max-width: 1024px) {
  .section-wrapper,
  .practice-wrapper,
  .puzzles-wrapper {
    grid-template-columns: 1fr;
    grid-template-areas:
      'header'
      'chessboard'
      'content' !important;
  }

  .chessboard-container {
    margin: 1rem 0;
  }
}

@media (max-width: 640px) {
  .practice-puzzles-section {
    padding: 2rem 0;
  }

  .section-wrapper {
    padding: 1.5rem;
  }

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
