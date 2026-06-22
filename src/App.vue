<template>
  <Header />

  <div class="main-content">
    <section class="separador" id="redes">
      <div class="hero-section">
        <div class="hero-text">
          <p class="description-text">
            Formado em Análise e Desenvolvimento de Sistemas, sou Engenheiro de Software com experiência em desenvolvimento back-end e full stack, APIs, integrações, bancos de dados e sistemas corporativos. Atuo com PHP, Symfony, Laravel, Java, Spring Boot, React, Docker, testes, code review e boas práticas de engenharia de software, com foco em qualidade, performance, aprendizado contínuo e entrega de soluções escaláveis.
          </p>

          <div class="social-links">
            <a
              v-for="link in links"
              :key="link.name"
              :href="link.url"
              class="redes-btn"
              :target="link.url.startsWith('mailto:') ? '_self' : '_blank'"
              rel="noopener noreferrer"
            >
              <i :class="`bi ${link.icon}`"></i>
              <span>{{ link.name }}</span>
            </a>
          </div>
        </div>

        <div class="hero-image">
          <img class="img-protifolio" src="/assets/img/Gustavo_1.jpeg" alt="Gustavo Luis Schmidt" />
        </div>
      </div>
    </section>

    <Tecnologias />
    <Repositorios />
  </div>
  <Footer />

  <div v-if="emailCopied" class="email-toast">
    <i class="bi bi-check-circle me-2"></i>
    Email copiado!
  </div>
</template>

<script setup>
import { ref } from "vue";
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
import Tecnologias from "./components/Tecnologias.vue";
import Repositorios from "./components/Repositorios.vue";

// Links fornecidos
const links = ref([
  {
    name: "Linkedin",
    url: "https://www.linkedin.com/in/gustavoluisschmidt/",
    icon: "bi-linkedin",
  },
  { name: "GitHub", url: "https://github.com/Gustavolskw", icon: "bi-github" },
  {
    name: "Email",
    url: "mailto:gustavolschmidt13@gmial.com",
    icon: "bi-envelope",
  },
]);

const emailCopied = ref(false);

// Função para copiar o email (se necessário)
const copyEmail = () => {
  // Copiar o email para a área de transferência
  navigator.clipboard.writeText("gustavolschmidt13@gmail.com").then(() => {
    emailCopied.value = true;
    setTimeout(() => (emailCopied.value = false), 2000); // Esconde a mensagem após 2 segundos
  });
};
</script>

<style scoped>
.main-content {
  min-height: 100vh;
  padding-top: 6rem;
}

.hero-section {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 4rem;
  padding: 0 2rem;
  max-width: 1100px;
  margin: 0 auto;
}

.hero-text {
  flex: 1;
  max-width: 600px;
  text-align: center;
}

.description-text {
  font-size: 1.1rem;
  line-height: 1.8;
  color: rgba(255, 255, 255, 0.7);
  font-weight: 300;
  letter-spacing: 0.01em;
}

.hero-image {
  flex: 0 0 auto;
  display: flex;
  justify-content: center;
}

.img-protifolio {
  width: 280px;
  height: 280px;
  border-radius: 50%;
  object-fit: cover;
  border: 3px solid rgba(0, 187, 201, 0.3);
  box-shadow: 
    0 0 0 8px rgba(0, 187, 201, 0.1),
    0 20px 60px rgba(0, 0, 0, 0.4);
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

.img-protifolio:hover {
  transform: scale(1.02);
  border-color: rgba(0, 187, 201, 0.5);
  box-shadow: 
    0 0 0 12px rgba(0, 187, 201, 0.15),
    0 25px 70px rgba(0, 0, 0, 0.5),
    0 0 40px rgba(0, 187, 201, 0.2);
}

.social-links {
  display: flex;
  gap: 1rem;
  margin-top: 2.5rem;
  justify-content: center;
  flex-wrap: wrap;
}

.redes-btn {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.875rem 1.5rem;
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.1) !important;
  border-radius: 12px;
  color: white !important;
  text-decoration: none;
  font-weight: 500;
  font-size: 0.95rem;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.redes-btn:hover {
  background: rgba(0, 187, 201, 0.1);
  border-color: rgba(0, 187, 201, 0.3) !important;
  transform: translateY(-2px);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
}

.redes-btn i {
  font-size: 1.25rem;
  color: var(--accent-color);
}

.email-toast {
  position: fixed;
  bottom: 2rem;
  left: 50%;
  transform: translateX(-50%);
  background: rgba(0, 187, 201, 0.15);
  border: 1px solid rgba(0, 187, 201, 0.3);
  backdrop-filter: blur(10px);
  padding: 1rem 2rem;
  border-radius: 12px;
  color: var(--accent-color);
  font-weight: 500;
  animation: slideUp 0.3s ease;
  z-index: 1000;
}

@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateX(-50%) translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateX(-50%) translateY(0);
  }
}

@media (max-width: 992px) {
  .hero-section {
    flex-direction: column-reverse;
    text-align: center;
    gap: 2rem;
  }

  .hero-text {
    max-width: 100%;
  }

  .social-links {
    justify-content: center;
  }

  .img-protifolio {
    width: 220px;
    height: 220px;
  }
}

@media (max-width: 576px) {
  .main-content {
    padding-top: 5rem;
  }

  .hero-section {
    padding: 0 1rem;
  }

  .description-text {
    font-size: 1rem;
  }

  .social-links {
    flex-direction: column;
    align-items: center;
  }

  .redes-btn {
    width: 100%;
    max-width: 280px;
    justify-content: center;
  }
}
</style>
