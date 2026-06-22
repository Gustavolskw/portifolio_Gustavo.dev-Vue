<template>
  <section id="tecnologias" class="separador">
    <div class="mb-5">
      <h2 class="text-center mb-4 fs-2 fw-bold section-title">Tecnologias</h2>
    </div>
    <div class="tech-grid">
      <div
        v-for="(tech, index) in techs"
        :key="index"
        class="tech-item"
      >
        <div class="tech-icon-wrapper">
          <img
            class="tech-icon"
            :src="`/assets/languages/${tech.icon}`"
            :alt="tech.name"
          />
        </div>
        <span class="tech-name">{{ tech.name }}</span>
      </div>
    </div>
  </section>
</template>

<script setup>
const techs = [
  { name: "PHP", icon: "php.png" },
  { name: "Java", icon: "java.png" },
  { name: "JavaScript", icon: "js.png" },
  { name: "TypeScript", icon: "ts.png" },
  { name: "Angular", icon: "Angular.png" },
  { name: "Vue", icon: "Vue.png" },
  { name: "MySQL", icon: "mysql.png" },
  { name: "PostgreSQL", icon: "postgre.png" },
  { name: "MongoDB", icon: "mongoDB.png" },
  { name: "Docker", icon: "docker.png" },
  { name: "Laravel", icon: "Laravel.png" },
  { name: "Spring Boot", icon: "springBoot.png" },
];
</script>

<style scoped>
.tech-grid {
  display: grid;
  grid-template-columns: repeat(6, 1fr);
  gap: 2rem;
  padding: 0 2rem;
  max-width: 1000px;
  margin: 0 auto;
}

.tech-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.75rem;
  cursor: pointer;
}

.tech-icon-wrapper {
  width: 70px;
  height: 70px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.06);
  border-radius: 16px;
  padding: 1rem;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.tech-item:hover .tech-icon-wrapper {
  background: rgba(0, 187, 201, 0.1);
  border-color: rgba(0, 187, 201, 0.3);
  transform: translateY(-4px);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
}

.tech-icon {
  width: 100%;
  height: 100%;
  object-fit: contain;
  transition: transform 0.3s ease;
}

.tech-item:hover .tech-icon {
  transform: scale(1.1);
}

.tech-name {
  font-size: 0.8rem;
  color: rgba(255, 255, 255, 0.5);
  font-weight: 500;
  text-align: center;
  transition: color 0.3s ease;
}

.tech-item:hover .tech-name {
  color: var(--accent-color);
}

@media (max-width: 768px) {
  .tech-grid {
    grid-template-columns: repeat(4, 1fr);
    gap: 1.5rem;
    padding: 0 1rem;
  }

  .tech-icon-wrapper {
    width: 60px;
    height: 60px;
  }
}

@media (max-width: 576px) {
  .tech-grid {
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem;
  }

  .tech-icon-wrapper {
    width: 50px;
    height: 50px;
    padding: 0.75rem;
  }

  .tech-name {
    font-size: 0.7rem;
  }
}
</style>
