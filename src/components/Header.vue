<template>
  <div class="d-flex justify-content-center">
    <nav
      class="navbar navbar-expand-lg nav-bar-theme py-5 d-flex flex-column"
      ref="navBar"
    >
      <div class="container-fluid justify-content-center">
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarNav"
          aria-controls="navbarNav"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div
          class="collapse navbar-collapse justify-content-center"
          id="navbarNav"
        >
          <div class="d-flex flex-column">
            <div class="d-flex align-items-center align-content-center gap-3">
              <i
                class="bi bi-code-slash fs-2 fw-bold text-white"
                style="text-shadow: 0px 0px 5px rgb(0, 187, 201)"
              ></i>
              <a class="nav-link fs-1 fw-bold" href="#">Gustavo Luis Schmidt</a>
            </div>
            <ul class="navbar-nav mb-2 mb-lg-0 justify-content-center gap-2">
              <li class="nav-item align-items-center align-content-center">
                <a class="nav-link" aria-current="page" href="#redes">Redes</a>
              </li>
              <li class="nav-item align-items-center align-content-center">
                <a class="nav-link" aria-current="page" href="#tecnologias"
                  >Linguagens</a
                >
              </li>
              <li class="nav-item align-items-center align-content-center">
                <a class="nav-link" aria-current="page" href="#projetos"
                  >Projetos</a
                >
              </li>
            </ul>
          </div>
        </div>
      </div>
      <div>
        <button
          class="btn text-white position-absolute d-none"
          @click="toggleNav"
          ref="btnHamb"
        >
          <i class="bi bi-justify fs-2 hamburger-nav rounded"></i>
        </button>
      </div>
    </nav>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";

const navBar = ref(null);
const btnHamb = ref(null);

let lastScrollY = 0;

const checkScroll = () => {
  if (!navBar.value || !btnHamb.value) return;

  if (window.scrollY > 200) {
    navBar.value.classList.add("nav-hide");
    btnHamb.value.classList.add("d-md-block");
  } else {
    if (window.scrollY < 100) {
      btnHamb.value.classList.remove("d-md-block");
    }
    if (window.scrollY > lastScrollY) {
      navBar.value.classList.add("nav-hide"); // Esconde ao rolar para baixo
    } else {
      navBar.value.classList.remove("nav-hide"); // Mostra ao rolar para cima
    }
  }
  lastScrollY = window.scrollY;
};

const toggleNav = () => {
  if (navBar.value.classList.contains("nav-hide")) {
    navBar.value.classList.remove("nav-hide");
  } else {
    navBar.value.classList.add("nav-hide");
  }
};

onMounted(() => {
  window.addEventListener("scroll", checkScroll);
});

onBeforeUnmount(() => {
  window.removeEventListener("scroll", checkScroll);
});
</script>

<style scoped>
.nav-bar-theme {
  z-index: 9999;
  background-color: transparent;
  position: fixed;
  backdrop-filter: blur(20px);
  background-color: #ffffff33;
  color: white;
  width: 70%;
  transition: transform 0.5s ease-in-out;
  border-bottom-right-radius: 10px;
  border-bottom-left-radius: 10px;
  font-family: "IBM Plex Mono", monospace !important;
  transform: translateY(-10%);
}

.nav-hide {
  transform: translateY(-85%);
}

.nav-link {
  font-size: 1.5rem;
  color: white !important;
  text-shadow: 0px 0px 5px rgb(0, 187, 201);
}

@media (max-width: 576px) {
  .nav-hide {
    transform: translateY(-93%);
  }
}
</style>
