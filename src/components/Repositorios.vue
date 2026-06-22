<template>
  <section id="projetos" class="separador mb-5">
    <div class="mb-5">
      <h2 class="text-center mb-5 fs-2 fw-bold section-title">
        Projetos Principais
      </h2>
    </div>

    <div class="projects-grid">
      <a
        v-for="project in projects"
        :key="project.name"
        :href="project.url"
        target="_blank"
        rel="noopener noreferrer"
        class="project-card"
      >
        <div class="project-card-inner">
          <div class="project-header">
            <i class="bi bi-folder2-open project-icon"></i>
            <i class="bi bi-box-arrow-up-right project-arrow"></i>
          </div>
          <h3 class="project-title">{{ project.name }}</h3>
          <span class="project-badge">{{ project.type }}</span>
          <p class="project-description">{{ project.description }}</p>
          <div class="project-techs">
            <span v-for="tech in project.techs" :key="tech" class="tech-tag">
              {{ tech }}
            </span>
          </div>
        </div>
      </a>
    </div>
  </section>
</template>

<script setup>
const projects = [
  {
    name: "AppFinancasNew",
    type: "Projeto de aprendizado",
    url: "https://github.com/Gustavolskw/FinancialAppNew",
    description:
      "Aplicação de finanças pessoais desenvolvida em monorepo, modelando carteiras, transações, entradas, despesas, tipos e métodos de pagamento com autenticação JWT e CRUD genérico configurável.",
    techs: ["PHP 8.4", "Symfony 8", "Doctrine ORM", "PostgreSQL", "React 19", "React Router 7", "TypeScript", "Vite", "Tailwind CSS", "Chart.js", "Docker", "NGINX"],
  },
  {
    name: "SimplePDVProject",
    type: "Projeto de aprendizado",
    url: "https://github.com/Gustavolskw/SimplePDVProject",
    description:
      "Projeto desenvolvido para treinar os principios simples de um ponto de vendas de uma lanchonete ou Foodtruck",
    techs: ["Vue", "JavaScript", "Java", "MySQL", "Docker"],
  },
  {
    name: "AuthServiceJava",
    type: "Projeto de aprendizado",
    url: "https://github.com/Gustavolskw/AuthServiceJava",
    description:
      "API Base de autenticação com Java e JWT para incluir em um projeto com arquitetura de microserviços",
    techs: ["Java", "MySQL", "JWT"],
  },
  {
    name: "EducaPlus-FrontEnd",
    type: "Projeto de aprendizado",
    url: "https://github.com/Gustavolskw/EducaPlus-FrontEnd",
    description:
      "Projeto desenvolvido durante o segundo ano da faculdade com a necessidade de auxiliar no desenvolvimento e avaliação de atividades escolares (Front-end)",
    techs: ["Angular", "TypeScript"],
  },
  {
    name: "EducaPlus-BackEnd",
    type: "Projeto de aprendizado",
    url: "https://github.com/Gustavolskw/EducaPlus-BackEnd",
    description:
      "Projeto desenvolvido durante o segundo ano da faculdade com a necessidade de auxiliar no desenvolvimento e avaliação de atividades escolares (Back-end)",
    techs: ["Java", "MySQL"],
  },
  {
    name: "Php-Serenatto-POO",
    type: "Projeto de aprendizado",
    url: "https://github.com/Gustavolskw/Php-Serenatto-POO",
    description:
      "Projeto desenvolvido durante cursos de aprendizado de PHP com boas práticas e uso do POO para fazer uma aplicação Fullstack",
    techs: ["PHP", "JavaScript"],
  },
];
</script>

<style scoped>
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
  gap: 1.5rem;
  padding: 0 2rem;
}

.project-card {
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 16px;
  padding: 2rem;
  text-decoration: none;
  color: inherit;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  overflow: hidden;
}

.project-card::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 2px;
  background: linear-gradient(90deg, transparent, var(--accent-color), transparent);
  opacity: 0;
  transition: opacity 0.3s ease;
}

.project-card:hover {
  transform: translateY(-4px);
  border-color: rgba(0, 187, 201, 0.3);
  background: rgba(255, 255, 255, 0.05);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3), 0 0 30px rgba(0, 187, 201, 0.1);
}

.project-card:hover::before {
  opacity: 1;
}

.project-card-inner {
  display: flex;
  flex-direction: column;
  height: 100%;
}

.project-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1.25rem;
}

.project-icon {
  font-size: 2rem;
  color: var(--accent-color);
}

.project-arrow {
  font-size: 1.25rem;
  color: rgba(255, 255, 255, 0.3);
  transition: all 0.3s ease;
}

.project-card:hover .project-arrow {
  color: var(--accent-color);
  transform: translate(3px, -3px);
}

.project-title {
  font-size: 1.25rem;
  font-weight: 600;
  color: white;
  margin-bottom: 0.5rem;
}

.project-badge {
  display: inline-block;
  font-size: 0.75rem;
  color: var(--accent-color);
  background: rgba(0, 187, 201, 0.1);
  padding: 0.25rem 0.75rem;
  border-radius: 20px;
  margin-bottom: 1rem;
  width: fit-content;
}

.project-description {
  font-size: 0.9rem;
  color: rgba(255, 255, 255, 0.6);
  line-height: 1.6;
  margin-bottom: 1.5rem;
  flex-grow: 1;
}

.project-techs {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.tech-tag {
  font-size: 0.7rem;
  color: rgba(255, 255, 255, 0.5);
  background: rgba(255, 255, 255, 0.05);
  padding: 0.35rem 0.65rem;
  border-radius: 6px;
  border: 1px solid rgba(255, 255, 255, 0.08);
}

@media (max-width: 768px) {
  .projects-grid {
    grid-template-columns: 1fr;
    padding: 0 1rem;
  }
}
</style>
