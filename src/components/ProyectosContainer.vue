<script setup>
import ProyectoSeguimiento from "./proyectos/ProyectoSeguimiento.vue";
import IconArrowGrande from "./icons/IconArrowGrande.vue";
import { ref } from "vue";
// Lista de proyectos
const projects = [
  {
    title: "Proyecto 1",
    description: "Descripción del proyecto 1.",
    tech: ["HTML5", "CSS3", "JavaScript"],
    liveUrl: "https://example.com/1",
    githubUrl: "https://github.com/usuario/proyecto1",
    images: [
      new URL("@/assets/img/proyecto-1.png", import.meta.url).href,
      new URL("@/assets/img/proyecto-2.png", import.meta.url).href,
      new URL("@/assets/img/proyecto-3.png", import.meta.url).href,
    ],
  },
  {
    title: "Proyecto 2",
    description: "Descripción del proyecto 2.",
    tech: ["Vue", "Tailwind"],
    liveUrl: "https://example.com/2",
    githubUrl: "https://github.com/usuario/proyecto2",
    images: [
      new URL("@/assets/img/proyecto-2.png", import.meta.url).href,
      new URL("@/assets/img/proyecto-2.png", import.meta.url).href,
    ],
  },
];

// Estado del índice actual
const current = ref(0);

// Navegación
function nextProject() {
  current.value = (current.value + 1) % projects.length;
}

function prevProject() {
  current.value = (current.value - 1 + projects.length) % projects.length;
}
function formatNumber(n) {
  return n < 10 ? `0${n}` : `${n}`;
}
</script>

<template>
  <h2 class="heading">Mis <span>Proyectos</span></h2>
  <div class="portfolios-container navegation-wrapper">
    <!-- Proyecto actual -->
    <ProyectoSeguimiento :project="projects[current]" :number="formatNumber(current + 1)" />
    <!-- Botones de navegación -->
    <div class="navegation">
      <button @click="prevProject" class="prev">
        <IconArrowGrande class="iconrev" />
      </button>
      <button @click="nextProject" class="next">
        <IconArrowGrande class="icon" />
      </button>
    </div>
  </div>
</template>

<style scoped>
.heading {
  font-size: 4.5rem;
  text-align: center;
  margin-bottom: 2rem;
}
.heading span {
  color: var(--main-color);
}
.navegation-wrapper {
  position: relative;
  padding-left: 6rem;
  padding-right: 4rem;
}

/* Contenedor de flechas */
.navegation {
  position: absolute;
  top: 50%;
  left: 0;
  width: 100%;
  display: flex;
  justify-content: space-between;
  transform: translateY(-50%);
  pointer-events: none; /* permite que botones internos reciban clics sin bloquear */
}

/* Flechas individuales */
.navegation button {
  pointer-events: all; /* reactiva clics solo en botones */
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0.5rem;
  background: var(--second-bg-color);
  border: 0.2rem solid var(--main-color);
  border-radius: 0.6rem;
  font-size: 4rem;
  color: var(--main-color);
  cursor: pointer;
  transition: background 0.2s ease;
}

.navegation button:hover {
  background: var(--main-color);
  color: #fff;
}

.navegation .prev {
  transform: rotate(180deg);
  margin-left: -2rem; /* opcional: para que salga un poco del contenedor */
}

.navegation .next {
  margin-right: -2rem; /* opcional */
}
</style>
