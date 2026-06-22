<template>
  <header class="header" ref="header">
    <nav class="nav-container">
      <a href="#" class="logo">
        <i class="bi bi-code-slash logo-icon"></i>
        <span class="logo-text">Gustavo Luis Schmidt</span>
      </a>

      <div class="nav-links" ref="navLinks">
        <a href="#redes" class="nav-link-item">Inicio</a>
        <a href="#tecnologias" class="nav-link-item">Tecnologias</a>
        <a href="#projetos" class="nav-link-item">Projetos</a>
      </div>

      <button
        class="mobile-menu-btn"
        @click="toggleMobileMenu"
        ref="menuBtn"
        aria-label="Toggle menu"
      >
        <i :class="`bi ${isMobileOpen ? 'bi-x-lg' : 'bi-list'}`"></i>
      </button>
    </nav>

    <div class="mobile-menu" :class="{ open: isMobileOpen }">
      <a href="#redes" class="mobile-link" @click="closeMobileMenu">Inicio</a>
      <a href="#tecnologias" class="mobile-link" @click="closeMobileMenu">Tecnologias</a>
      <a href="#projetos" class="mobile-link" @click="closeMobileMenu">Projetos</a>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";

const header = ref(null);
const menuBtn = ref(null);
const isMobileOpen = ref(false);
let lastScrollY = 0;
let isHidden = false;

const checkScroll = () => {
  if (!header.value) return;

  const currentScrollY = window.scrollY;

  if (currentScrollY > 100) {
    if (currentScrollY > lastScrollY && !isHidden) {
      header.value.classList.add("header-hidden");
      isHidden = true;
    } else if (currentScrollY < lastScrollY && isHidden) {
      header.value.classList.remove("header-hidden");
      isHidden = false;
    }
  } else {
    header.value.classList.remove("header-hidden");
    isHidden = false;
  }

  lastScrollY = currentScrollY;
};

const toggleMobileMenu = () => {
  isMobileOpen.value = !isMobileOpen.value;
};

const closeMobileMenu = () => {
  isMobileOpen.value = false;
};

onMounted(() => {
  window.addEventListener("scroll", checkScroll, { passive: true });
});

onBeforeUnmount(() => {
  window.removeEventListener("scroll", checkScroll);
});
</script>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  padding: 1rem 2rem;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  background: rgba(26, 26, 46, 0.9);
  backdrop-filter: blur(20px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
}

.header-hidden {
  transform: translateY(-100%);
}

.nav-container {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.logo {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  text-decoration: none;
  color: white;
}

.logo-icon {
  font-size: 1.75rem;
  color: var(--accent-color);
}

.logo-text {
  font-size: 1.25rem;
  font-weight: 600;
  letter-spacing: -0.02em;
}

.nav-links {
  display: flex;
  gap: 2.5rem;
}

.nav-link-item {
  color: rgba(255, 255, 255, 0.7);
  text-decoration: none;
  font-size: 0.95rem;
  font-weight: 500;
  transition: color 0.3s ease;
  position: relative;
}

.nav-link-item::after {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 0;
  width: 0;
  height: 2px;
  background: var(--accent-color);
  transition: width 0.3s ease;
}

.nav-link-item:hover {
  color: white;
}

.nav-link-item:hover::after {
  width: 100%;
}

.mobile-menu-btn {
  display: none;
  background: none;
  border: none;
  color: white;
  font-size: 1.5rem;
  cursor: pointer;
  padding: 0.5rem;
}

.mobile-menu {
  display: none;
  position: absolute;
  top: 100%;
  left: 0;
  right: 0;
  background: rgba(26, 26, 46, 0.98);
  backdrop-filter: blur(20px);
  padding: 1rem 2rem;
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
  transform: translateY(-10px);
  opacity: 0;
  visibility: hidden;
  transition: all 0.3s ease;
}

.mobile-menu.open {
  transform: translateY(0);
  opacity: 1;
  visibility: visible;
}

.mobile-link {
  display: block;
  color: rgba(255, 255, 255, 0.7);
  text-decoration: none;
  font-size: 1rem;
  font-weight: 500;
  padding: 1rem 0;
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
  transition: color 0.3s ease;
}

.mobile-link:last-child {
  border-bottom: none;
}

.mobile-link:hover {
  color: var(--accent-color);
}

@media (max-width: 768px) {
  .nav-links {
    display: none;
  }

  .mobile-menu-btn {
    display: block;
  }

  .mobile-menu {
    display: block;
  }

  .header {
    padding: 1rem 1.5rem;
  }
}
</style>
