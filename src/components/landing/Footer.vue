<template>
  <footer class="footer">
    <div class="footer-content">
      <div class="copyright">© Chessiverse 2024-2025.</div>
      <div class="footer-links">
        <a href="#">Contact Us</a>
        <span class="divider">|</span>
        <a href="#">PersonaPlay™</a>
        <span class="divider">|</span>
        <a href="#">About Us</a>
        <span class="divider">|</span>
        <a href="#">Blog</a>
        <span class="divider">|</span>
        <a href="#">Join our Discord</a>
        <span class="divider">|</span>
        <a href="#">Terms</a>
        <span class="divider">|</span>
        <a href="#">Privacy</a>
      </div>
    </div>
  </footer>
</template>

<script setup lang="ts"></script>

<style scoped>
.footer {
  background-color: var(--clr-background-accent);
  padding: 1.5rem 0;
  text-align: center;
}

.footer-content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
}

.copyright {
  margin-bottom: 0.5rem;
  font-weight: 500;
  font-size: 1rem;
}

.footer-links {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 0.5rem;
  font-size: 1rem;
}

.footer-links a {
  font-weight: 500;
  text-decoration: underline;
}

.divider {
  color: #666;
  margin: 0 0.25rem;
}

@media (max-width: 600px) {
  .footer-links {
    flex-direction: column;
    align-items: center;
  }

  .divider {
    display: none;
  }
}
</style>
