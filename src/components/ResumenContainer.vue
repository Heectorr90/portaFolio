<script setup>
// Componente ResumenContainer.vue
import { ref } from "vue";
// Importar los iconos de habilidades
import IconVue from "./icons/habilidades/IconVue.vue";
import IconLaravel from "./icons/habilidades/IconLaravel.vue";
import IconPHP from "./icons/habilidades/IconPHP.vue";
import IconMySQL from "./icons/habilidades/IconMySQL.vue";
import IconGit from "./icons/habilidades/IconGit.vue";
import IconHTML from "./icons/habilidades/IconHTML.vue";
import IconCSS from "./icons/habilidades/IconCSS.vue";
import IconJavaScript from "./icons/habilidades/IconJavaScript.vue";
import IconAngular from "./icons/habilidades/IconAngular.vue";
// Título y descripción del componente
const title = "¿Por qué contratarme?";
const description = "Aquí hay algunas razones para considerar mi contratación:";
const activeTab = ref("experiencia");
// Definición de las pestañas y sus contenidos
const tabs = ["Experiencia", "Educación", "Habilidades", "Información"];
// Datos de experiencia, educación, habilidades e información personal
const experiencia = [
  {
    year: "2022 - Presente",
    title: "Desarrollador Web Jr.",
    company: 'Bit Electronics "Centro de servicio"',
    description:
      "Automatización, monitoreo y resolución de incidencias técnicas de tareas repetitivas mediante scripts y herramientas de backend para mejorar la productividad.",
  },
  {
    year: "2021 - 2022",
    title: "Programador front-end",
    company: "CTED Corporativo Tecnológico y Educativo S.A. de C.V.",
    description:
      "Durante mi estancia como becario, participé en el desarrollo y mantenimiento de aplicaciones web utilizando tecnologías como HTML, CSS y Angular.",
  },
];
const educacion = [
  {
    year: "2023 - 2024",
    title: "Ingeniería en Sistemas Computacionales",
    company: "Tecnológico Universitario de Toluca.",
    description: "Enfoque en desarrollo de software, bases de datos y administración de sistemas.",
  },
  {
    year: "2016 - 2019",
    title: "Ingeniería Informática (Trunca)",
    company: "Tecnológico Universitario de Toluca.",
    description:
      "Formación en lógica de programación, redes y fundamentos de ingeniería. Se cursaron materias clave antes de la interrupción de estudios.",
  },
];
const skills = [
  { name: "HTML5", icon: IconHTML },
  { name: "CSS3", icon: IconCSS },
  { name: "JavaScript", icon: IconJavaScript },
  { name: "Vue.js", icon: IconVue },
  { name: "Laravel", icon: IconLaravel },
  { name: "PHP", icon: IconPHP },
  { name: "MySQL", icon: IconMySQL },
  { name: "Git y GitHub", icon: IconGit },
  { name: "Angular", icon: IconAngular },
];
const informacionPersonal = [
  { label: "Nombre", value: "Héctor Ramírez" },
  { label: "Edad", value: "29 años" },
  { label: "Estado", value: "Soltero" },
  { label: "Ubicación", value: "Estado de México, Toluca" },
  { label: "Correo", value: "hector@example.com" },
  { label: "Lenguaje", value: "Español, Inglés (Básico)" },
];
</script>

<template>
  <div class="resume-container">
    <div class="resume-box">
      <h2>{{ title }}</h2>
      <p class="desc">{{ description }}</p>
      <button
        v-for="tab in tabs"
        :key="tab"
        class="resume-btn"
        :class="{ active: activeTab === tab }"
        @click="activeTab = tab"
      >
        {{ tab }}
      </button>
    </div>
    <div class="resume-box">
      <!-- EXPERIENCIA -->
      <div class="resume-detail" v-if="activeTab === 'Experiencia'">
        <h2 class="heading">Mi <span>Experiencia</span></h2>
        <p class="desc">
          He trabajado en diversos proyectos que me han permitido crecer como desarrollador web.
        </p>
        <div class="resume-list">
          <div class="resume-item" v-for="(item, index) in experiencia" :key="index">
            <p class="year">{{ item.year }}</p>
            <h3>{{ item.title }}</h3>
            <p class="company">{{ item.company }}</p>
            <p>{{ item.description }}</p>
          </div>
        </div>
      </div>
      <!-- EDUCACIÓN -->
      <div class="resume-detail" v-else-if="activeTab === 'Educación'">
        <h2 class="heading">Mi <span>Educación</span></h2>
        <p class="desc">Formación académica y cursos que respaldan mis conocimientos técnicos.</p>
        <div class="resume-list">
          <div class="resume-item" v-for="(item, index) in educacion" :key="index">
            <p class="year">{{ item.year }}</p>
            <h3>{{ item.title }}</h3>
            <p class="company">{{ item.company }}</p>
            <p>{{ item.description }}</p>
          </div>
        </div>
      </div>
      <!-- HABILIDADES -->
      <div class="resume-detail skills" v-else-if="activeTab === 'Habilidades'">
        <h2 class="heading">Mis <span>Habilidades</span></h2>
        <p class="desc">
          Competencias técnicas que domino y aplico en mis proyectos de desarrollo.
        </p>
        <div class="resume-list">
          <div class="resume-item" v-for="skill in skills" :key="skill.name">
            <component :is="skill.icon" class="icon" />
            <span class="skill-name">{{ skill.name }}</span>
          </div>
        </div>
      </div>
      <!-- INFORMACIÓN -->
      <div class="resume-detail about" v-else-if="activeTab === 'Información'">
        <h2 class="heading">Mi <span>Información</span></h2>
        <p class="desc">
          A continuación, te comparto mis datos personales y de contacto para que puedas comunicarte
          conmigo de manera directa y eficiente.
        </p>
        <div class="resume-list">
          <div class="resume-item" v-for="(item, index) in informacionPersonal" :key="index">
            <p>
              {{ item.label }}: <span>{{ item.value }}</span>
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.resume-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 5rem;
}
.resume-box h2 {
  font-size: 4.5rem;
}
.resume-box p {
  font-size: 1.6rem;
}
.resume-box .desc {
  margin: 2rem 0 2.5rem;
}
.resume-box .resume-btn {
  width: 100%;
  height: 5.3rem;
  background: var(--second-bg-color);
  border: 0.2rem solid var(--second-bg-color);
  font-size: 1.6rem;
  color: var(--text-color);
  font-weight: 500;
  margin-bottom: 2rem;
  border-radius: 0.8rem;
  cursor: pointer;
  transition: 0.3s;
}
.resume-box .resume-btn.active {
  border-color: var(--main-color);
  color: var(--main-color);
}

.resume-box .heading {
  font-size: 3.5rem;
  text-align: left;
}
.resume-box .heading span {
  color: var(--main-color);
}
.resume-list {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(30rem, 1fr));
  gap: 2rem;
  height: 45rem;
  overflow: auto;
}
.resume-list::-webkit-scrollbar {
  width: 0.7rem;
}
.resume-list::-webkit-scrollbar-thumb {
  background: transparent;
  border-radius: 1rem;
}
.resume-list:hover::-webkit-scrollbar-thumb {
  background: var(--main-color);
}
.resume-list .resume-item {
  background: var(--second-bg-color);
  border-radius: 0.8rem;
  padding: 3rem 2.5rem;
  height: calc((45rem - 2rem) / 2);
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.resume-item .year {
  color: var(--main-color);
}
.resume-item h3 {
  font-size: 2.2rem;
}
.resume-item .company {
  position: relative;
  margin-left: 2rem;
  margin-bottom: 2rem;
}
.resume-item .company::before {
  content: "";
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  padding: 0.5rem;
  background: var(--main-color);
  border-radius: 50%;
  margin-left: -2rem;
}
.resume-detail.skills .resume-list {
  grid-template-columns: repeat(auto-fit, minmax(15rem, 1fr));
  height: auto;
  overflow: visible;
}
.resume-detail.skills .resume-item {
  position: relative;
  align-items: center;
  height: auto;
}
.resume-detail.skills .resume-item .icon {
  font-size: 10rem;
  transition: 0.5s;
}
.resume-detail.skills .resume-item:hover .icon {
  color: var(--main-color);
}
.resume-detail.skills .resume-item span {
  position: absolute;
  top: -20%;
  background: var(--text-color);
  color: var(--second-bg-color);
  font-size: 1.6rem;
  padding: 0.5rem 1rem;
  border-radius: 0.6rem;
  pointer-events: none;
  opacity: 0;
  transform: scale(0.9);
  transition: 0.2s;
}
.resume-detail.skills .resume-item:hover span {
  top: -25%;
  opacity: 1;
  transform: scale(1);
}
.resume-detail.about .resume-list {
  height: auto;
  grid-template-columns: repeat(auto-fit, minmax(25rem, 1fr));
}
.resume-detail.about .resume-item {
  height: auto;
  padding: 0 0 0.5rem;
  background: transparent;
}
.resume-detail.about .resume-item p {
  color: var(--main-color);
}
.resume-detail.about .resume-item p span {
  color: var(--text-color);
  margin-left: 1rem;
  font-size: 1.8rem;
}
</style>
