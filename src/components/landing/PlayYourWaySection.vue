<!-- eslint-disable @typescript-eslint/no-explicit-any -->
<script setup lang="ts">
import { ref } from 'vue'
import AccentedText from '@/components/ui/AccentedText.vue';
import UIButton from '@/components/ui/UIButton.vue'

const gameType = ref<string>('rated');

function toggleGameType(type: string) {
  gameType.value = type
}
</script>

<template>
  <section class="your-way-section">
    <div class="container">
      <h2 class="section-title">
        <AccentedText text="Play Your Way - "/>
        <span class="text-accent">&nbsp;Rated or Casual,</span><br />
        <span class="text-accent">Fast or Slow</span>
      </h2>

      <div class="game-options-container">
        <div class="game-mode-switcher shadow-card">
            <div
              class="switcher-item"
              :class="{'active-item': gameType === 'rated'}"
              @click="toggleGameType('rated')"
            >
              Rated
            </div>
            <div
              class="switcher-item"
              :class="{'active-item': gameType === 'casual'}"
              @click="toggleGameType('casual')"
            >
              Casual
            </div>
        </div>

        <div class="game-features-list">
          <div class="game-features-item shadow-card">
            <div class="game-feature-image">
              <img src="/img/gameFeatures/bullet.png" alt="bullet">
            </div>
            <div class="game-feature-info">
              <div class="title">Bullet</div>
              <div class="description">for lightning-fast moves</div>
            </div>
          </div>

          <div class="game-features-item shadow-card">
            <div class="game-feature-image">
              <img src="/img/gameFeatures/biltz.png" alt="biltz">
            </div>
            <div class="game-feature-info">
              <div class="title">Biltz</div>
              <div class="description">or quick strategy</div>
            </div>
          </div>

          <div class="game-features-item shadow-card">
            <div class="game-feature-image">
              <img src="/img/gameFeatures/rapid.png" alt="rapid">
            </div>
            <div class="game-feature-info">
              <div class="title">Rapid</div>
              <div class="description">or thoughtful play</div>
            </div>
          </div>
        </div>

        <div style="display: flex; justify-content: center; margin-top: 2.5rem">
          <UIButton size="lg" icon="/svg/swords.svg" text="Play now" />
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.your-way-section {
  padding: 5rem 0 1rem;
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
  margin-bottom: 1rem;
  line-height: 1.2;

  span {
    font-weight: 800;
  }

  .text-accent {
    color: var(--clr-accent);
  }
}

.shadow-card{
  background: white;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.08);
  transition:
    transform 0.3s ease,
    box-shadow 0.3s ease;
  position: relative;
}

.game-options-container {
  padding: 1rem 0 2rem;
  width: 350px;
  margin: 0 auto;

  .game-mode-switcher{
    display: flex;
    height: 50px;
    background-color: var(--clr-inactive-bg);

    .switcher-item{
      width: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      font-weight: 600;
      cursor: pointer;
    }

    .active-item{
      background-color: white;
    }
  }

  .game-features-list{
    margin-top: 1rem;
    display: flex;
    flex-direction: column;
    gap: 0.4rem;

    .game-features-item {
      padding: 0.5rem;
      display: flex;
      align-items: center;
      gap: 1rem;

      .game-feature-image{
        margin-top: 0.5rem;
      }

      .game-feature-info {
        line-height: 1.2;
        .title {
          font-weight: 600;
        }
      }
    }
  }
}

@media (max-width: 768px) {
  .section-title {
    font-size: 2rem;
    margin-bottom: 2rem;
  }
}

@media (max-width: 405px) {
  .game-options-container {
    width: 320px;
  }
}

@media (max-width: 366px) {
  .game-options-container {
    width: 300px;
  }
}
</style>
