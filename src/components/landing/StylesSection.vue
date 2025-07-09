<template>
  <section class="styles-section">
    <div class="container">
      <div class="header">
        <h2>Custom Opening Repertoirs & <br /><span>Unique Styles</span></h2>
        <p>
          Every bot starts differently—just like real players. Each has a unique opening book built
          from millions of human games, tailored to match their style and strength.
        </p>
      </div>

      <div class="style-cards-container">
        <picture>
          <source media="(max-width: 600px)" srcset="/img/styles/playstyles_mobile.svg" />
          <img src="/img/styles/playstyles.webp" alt="Chess playstyles" class="style-cards" />
        </picture>
      </div>

      <div class="style-details">
        <img src="/img/styles/meter.webp" alt="Rating" class="meter" />
        <img src="/img/styles/chart.webp" alt="Style Chart" class="chart" />
        <img src="/img/styles/repertoire.webp" alt="Repertoire" class="repertoire" />
      </div>
    </div>
  </section>
</template>

<script setup lang="ts"></script>

<style scoped>
.styles-section {
  position: relative;
  overflow: hidden;
}

.container {
  width: 100%;
  margin: 0 auto;
  padding: var(--container-padding-desktop);
  position: relative;
  background: url('/img/styles/styles_bg.webp') no-repeat;
  background-position: center center;
  background-size: contain;
  z-index: 2;
}

.header {
  text-align: left;
  max-width: 1000px;
  margin: 0 0 3.75rem 0;
}

.header h2 {
  font-size: 2.5rem;
  margin: 0 0 1.25rem;
  font-weight: 700;
  line-height: 1.2;
}

.header h2 span {
  font-weight: 800;
  color: var(--clr-accent);
}

.header p {
  font-size: 1.1rem;
  line-height: 1.6;
  margin: 0 auto;
  max-width: 700px;
  font-family: var(--font-handwritten);
  text-align: center;
}

.style-cards-container {
  width: 100%;
  max-width: 1000px;
  margin: 0 0 3.125rem 0;
  padding: 0;
}

.style-cards {
  width: 100%;
  height: auto;
  display: block;
  margin: 0 auto;
}

.style-details {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  gap: 1rem;
  margin-top: 1.875rem;
}

.meter,
.chart,
.repertoire {
  width: 380px;
  height: auto;
  border-radius: 1rem;
}

/* Responsive adjustments */
@media screen and (max-width: 1280px) {
  .container {
    padding: var(--container-padding-tablet);
  }
}

@media screen and (max-width: 1024px) {
  .container {
    background-position: center bottom;
  }
  .style-details {
    flex-direction: column;
  }
}

@media screen and (max-width: 768px) {
  .styles-section {
    padding: 4rem 0;
  }

  .header h2 {
    font-size: 2rem;
  }

  .header p {
    font-size: 1rem;
  }

  .style-cards-container {
    margin-bottom: 2rem;
    padding: 0 0.5rem;
  }

  .style-cards-container img {
    width: 100%;
    height: auto;
  }
}

@media screen and (max-width: 480px) {
  .container {
    padding: var(--container-padding-mobile);
  }

  .header h2 {
    font-size: 1.75rem;
  }

  .header p {
    font-size: 0.95rem;
  }

  .meter,
  .chart,
  .repertoire {
    width: 250px;
  }
}
</style>
