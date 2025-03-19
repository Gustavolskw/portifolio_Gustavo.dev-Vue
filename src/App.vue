<template>
  <Header />

  <div class="mx-md-5 mx-1 h-100 main-content">
    <section class="d-flex justify-content-center">
      <div class="flex-column">
        <p class="fs-4 text-center">
          <q style="text-shadow: 0px 0px 5px rgb(0, 187, 201)">
            Eu creio que um dos princípios essenciais da sabedoria é o de se
            abster das ameaças verbais ou insultos.
          </q>
        </p>
        <p class="fs-5 ps-4">Maquiavel</p>
      </div>
    </section>

    <section class="row separador w-100 mx-md-4 content" id="redes">
      <div class="col-md-7 h-100 mb-md-1 mb-5 ms-md-0 ms-2">
        <div
          class="justify-content-center d-flex align-content-center h-75 pt-5"
        >
          <p class="fs-3 text-center fw-bold">
            Cursando Análise e Desenvolvimento de Sistemas, com foco em
            desenvolvimento Back-end, banco de dados e Front-end. Possuo
            habilidades em resolução de problemas, aprendizado rápido e
            adaptação a novas tecnologias. Busco oportunidades para aplicar meu
            conhecimento em uma empresa de tecnologia em crescimento.
          </p>
        </div>

        <div
          class="d-flex gap-md-5 justify-content-center mt-5 flex-wrap gap-md-1 gap-4"
        >
          <div v-for="link in links" :key="link.name">
            <button
              v-if="link.name === 'Email'"
              @click="copyEmail"
              class="btn text-white d-flex align-items-center align-content-center justify-content-center border-white redes-btn"
            >
              <i :class="`bi fs-3 ${link.icon}`"></i>
              <h2 class="mt-1">{{ link.name }}</h2>
            </button>
            <a
              v-else
              class="btn text-white d-flex align-items-center align-content-center justify-content-center border-white redes-btn"
              :href="link.url"
            >
              <i :class="`bi fs-3 ${link.icon}`"></i>
              <h2 class="mt-1">{{ link.name }}</h2>
            </a>
          </div>
        </div>

        <div
          v-if="emailCopied"
          class="alert bg-transparent alert-info text-info w-50 mt-2 mx-auto"
          role="alert"
        >
          Email Copiado!
        </div>
      </div>

      <div class="col-md-5">
        <div class="img-container d-flex justify-content-center h-100">
          <img class="img-protifolio" src="/assets/img/Gustavo_1.jpeg" alt="" />
        </div>
      </div>
    </section>

    <Tecnologias />
    <Repositorios />
  </div>
  <Footer />
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
  padding-top: 14rem;
}
.img-protifolio {
  border-radius: 380px;
  width: 60%;
  box-shadow: 15px 15px 50px rgb(0, 187, 201);
  animation: box-squeeze 15s infinite, pulse-shadow 6s infinite alternate;
}

@keyframes pulse-shadow {
  0% {
    box-shadow: 15px 15px 50px rgb(0, 187, 201);
  }

  50% {
    box-shadow: 25px 25px 70px rgb(0, 187, 201);
  }

  100% {
    box-shadow: 15px 15px 50px rgb(0, 187, 201);
  }
}

/* Existing box-squeeze animation (you can adjust it) */
@keyframes box-squeeze {
  0% {
    transform: scale(1);
  }

  50% {
    transform: scale(1.0004);
  }

  100% {
    transform: scale(1);
  }
}

.redes-btn:hover {
  box-shadow: 5px 5px 15px rgb(0, 187, 201);
  animation: pulse-shadow-btn 4s infinite alternate;
  transform: scale(1.1);
}

@keyframes pulse-shadow-btn {
  0% {
    box-shadow: 5px 5px 15px rgb(0, 187, 201);
  }

  50% {
    box-shadow: 5px 5px 25px rgb(0, 187, 201);
  }

  100% {
    box-shadow: 5px 5px 15px rgb(0, 187, 201);
  }
}

#emailAlert {
  display: none;
  padding: 10px;
  background-color: rgba(0, 123, 255, 0.1);
  border: 1px solid #007bff;
  color: #007bff;
  border-radius: 5px;
  text-align: center;
  font-size: 16px;
  font-weight: bold;
  transition: opacity 0.5s ease, visibility 0s linear 0.5s;
}

#copyButton {
  transition: transform 0.3s ease, background-color 0.3s ease;
}

@media (max-width: 1200px) {
  .img-protifolio {
    width: 90%;
    height: 85%;
  }
}

@media (max-width: 992px) {
  .img-protifolio {
    width: 100%;
    height: 70%;
    animation: pulse-shadow 6s infinite alternate;
  }
}

@media (max-width: 768px) {
  .img-protifolio {
    width: 60%;
    height: 90%;
  }

  .main-content {
    padding-top: 10rem;
  }
}

@media (max-width: 576px) {
  .nav-bar-theme {
    width: 100% !important;
  }
  .img-protifolio {
    width: 60%;
  }
}
</style>
