<template>
  <footer class="footer">
    <div class="footer-content">
      <div class="footer-section">
        <span class="footer-label">Github</span>
        <a href="https://github.com/Gustavolskw" target="_blank" rel="noopener noreferrer" class="footer-link">
          Gustavolskw
        </a>
      </div>

      <div class="footer-divider"></div>

      <div class="footer-section">
        <span class="footer-label">Tecnologias do Portfólio</span>
        <div class="footer-techs">
          <img class="footer-tech-icon" src="/assets/languages/Vue.png" alt="Vue" />
          <img class="footer-tech-icon" src="/assets/languages/js.png" alt="JavaScript" />
          <img class="footer-tech-icon" src="/assets/languages/css.png" alt="CSS" />
          <img class="footer-tech-icon" src="/assets/languages/bootstrap.png" alt="Bootstrap" />
        </div>
      </div>
    </div>

    <div class="footer-bottom">
      <p>&copy; {{ currentYear }} Gustavo Luis Schmidt. Todos os direitos reservados.</p>
    </div>
  </footer>
</template>

<script setup>
const currentYear = new Date().getFullYear();
</script>

<style scoped>
.footer {
  margin-top: 6rem;
  padding: 3rem 2rem 1.5rem;
  border-top: 1px solid rgba(255, 255, 255, 0.08);
  background: rgba(26, 26, 46, 0.9);
  backdrop-filter: blur(20px);
}

.footer-content {
  max-width: 800px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 3rem;
  flex-wrap: wrap;
}

.footer-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.75rem;
}

.footer-label {
  font-size: 0.75rem;
  color: rgba(255, 255, 255, 0.5);
  text-transform: uppercase;
  letter-spacing: 0.1em;
  font-weight: 500;
}

.footer-link {
  color: rgba(255, 255, 255, 0.8);
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s ease;
}

.footer-link:hover {
  color: var(--accent-color);
}

.footer-divider {
  width: 1px;
  height: 40px;
  background: rgba(255, 255, 255, 0.15);
}

.footer-techs {
  display: flex;
  gap: 1rem;
  align-items: center;
}

.footer-tech-icon {
  width: 28px;
  height: 28px;
  opacity: 0.6;
  transition: opacity 0.3s ease, transform 0.3s ease;
}

.footer-tech-icon:hover {
  opacity: 1;
  transform: scale(1.1);
}

.footer-bottom {
  margin-top: 2rem;
  padding-top: 1.5rem;
  border-top: 1px solid rgba(255, 255, 255, 0.08);
  text-align: center;
}

.footer-bottom p {
  font-size: 0.8rem;
  color: rgba(255, 255, 255, 0.4);
  margin: 0;
}

@media (max-width: 576px) {
  .footer-content {
    flex-direction: column;
    gap: 2rem;
  }

  .footer-divider {
    width: 40px;
    height: 1px;
  }
}
</style>
