<template>
  <section id="tecnologias" class="separador">
    <div class="mb-5">
      <h2 class="text-center mb-4 fs-2 fw-bold section-title">Tecnologias</h2>
    </div>
    <div class="row justify-content-center mx-1 gap-5 pt-3">
      <div
        class="col-md-2 col-4 d-flex justify-content-center"
        v-for="(tech, index) in techs"
        :key="index"
      >
        <img
          class="img-tech"
          :class="`icon-tech${index}`"
          :src="`/assets/languages/${tech.icon}`"
          :alt="`Ícone do(a) ${tech.name}`"
        />
      </div>
    </div>
  </section>
</template>

<script setup>
const techs = [
  { name: "PHP", icon: "php.png" },
  { name: "Java", icon: "java.png" },
  { name: "Javascript", icon: "js.png" },
  { name: "TypeScript", icon: "ts.png" },
  { name: "Angular", icon: "Angular.png" },
  { name: "Vue", icon: "Vue.png" },
  { name: "Mysql", icon: "mysql.png" },
  { name: "PostgreSQL", icon: "postgre.png" },
  { name: "MongoDB", icon: "mongoDB.png" },
  { name: "Docker", icon: "docker.png" },
  { name: "Laravel", icon: "Laravel.png" },
  { name: "Spring Boot", icon: "springBoot.png" },
];
</script>

<style scoped>
.img-tech {
  cursor: pointer;
  width: 25%;
}

.img-tech:hover {
  animation: none;
  transform: scale(1.09);
}

@keyframes float {
  0% {
    transform: translateY(0);
    transform: translateX(0);
  }

  50% {
    transform: translateY(-20px);
    transform: translateX(-20);
  }

  100% {
    transform: translateY(0);
    transform: translateX(0);
  }
}

.icon-tech0 {
  animation: float 6s ease-in-out infinite;
}

.icon-tech1 {
  animation: float 6s ease-in-out infinite;
  animation-delay: 1s;
}

.icon-tech2 {
  animation: float 6s ease-in-out infinite;
  animation-delay: 2s;
}

.icon-tech3 {
  animation: float 6s ease-in-out infinite;
  animation-delay: 3s;
}

.icon-tech4 {
  animation: float 6s ease-in-out infinite;
  animation-delay: 4s;
}

.icon-tech5 {
  animation: float 6s ease-in-out infinite;
  animation-delay: 2s;
}

.icon-tech6 {
  animation: float 6s ease-in-out infinite;
  animation-delay: 6s;
}

.icon-tech7 {
  animation: float 6s ease-in-out infinite;
  animation-delay: 0s;
}

.icon-tech8 {
  animation: float 6s ease-in-out infinite;
  animation-delay: 3s;
}

.icon-tech9 {
  animation: float 6s ease-in-out infinite;
  animation-delay: 6s;
}

.icon-tech9 {
  animation: float 6s ease-in-out infinite;
  animation-delay: 3s;
}

.icon-tech10 {
  animation: float 6s ease-in-out infinite;
  animation-delay: 5s;
}

.icon-tech11 {
  animation: float 6s ease-in-out infinite;
  animation-delay: 1s;
}

@media (max-width: 768px) {
  .img-tech {
    cursor: pointer;
    width: 50%;
  }
}

@media (max-width: 576px) {
  .img-tech {
    cursor: pointer;
    width: 75%;
  }
}
</style>
