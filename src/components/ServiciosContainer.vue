<script setup>
// Importing icons for services
import IconFlechaAtras from "./icons/servicios/IconFlechaAtras.vue";
import IconProgramming from "./icons/servicios/IconProgramming.vue";
import IconUI from "./icons/servicios/IconUI.vue";
import IconApi from "./icons/servicios/IconApi.vue";
import IconBD from "./icons/servicios/IconBD.vue";
import IconMaintenance from "./icons/servicios/IconMaintenance.vue";
import IconAutomation from "./icons/servicios/IconAutomation.vue";
// Importing Vue's ref for reactivity
import { ref } from "vue";
const Servicios = ref([
  {
    id: 1,
    name: "Desarrollo Web",
    descripcion: "Desarrollo de aplicaciones web",
    icon: IconProgramming,
  },
  {
    id: 2,
    name: "Integración de APIs",
    descripcion:
      "Conexión con servicios externos como pasarelas de pago, redes sociales o sistemas de terceros mediante APIs REST o GraphQL.",
    icon: IconApi, // o algo como plug/cable
  },
  {
    id: 3,
    name: "Automatización de Procesos",
    descripcion:
      "Automatización de tareas repetitivas mediante scripts y herramientas de backend para mejorar la productividad.",
    icon: IconAutomation,
  },
  {
    id: 4,
    name: "UI/UX Design",
    descripcion:
      "se refiere a la experiencia del usuario (UX) y la interfaz del usuario (UI) en el contexto del desarrollo de productos digitales, como sitios web y aplicaciones.",
    icon: IconUI,
  },
  {
    id: 5,
    name: "Bases de Datos",
    descripcion:
      "Diseño, implementación y optimización de bases de datos relacionales y no relacionales para proyectos web",
    icon: IconBD,
  },
  {
    id: 6,
    name: "Mantenimiento y Soporte",
    descripcion:
      "Actualización, monitoreo y resolución de incidencias técnicas en sistemas en producción.",
    icon: IconMaintenance,
  },
]);
</script>

<template>
  <h2 class="heading">Mis <span>Servicios</span></h2>
  <div class="services-container">
    <div class="services-box" v-for="ser in Servicios" :key="ser.id" :href="ser.href">
      <div class="icon">
        <component :is="ser.icon" class="icon-main" />
        <a href=""><iconFlechaAtras class="icon-arrow" /></a>
      </div>
      <h3 class="service-title">{{ ser.name }}</h3>
      <p class="service-description">{{ ser.descripcion }}</p>
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
.services-container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(30rem, 1fr));
  gap: 2rem;
}
.services-container .services-box {
  padding: 3rem 2.5rem;
  background: var(--second-bg-color);
  border: 0.2rem solid var(--second-bg-color);
  border-radius: 1rem;
  transition: 0.5s;
}
.services-container .services-box:hover {
  border-color: var(--main-color);
  transform: scale(1.02);
}
.services-box .icon {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.services-box .icon .icon-main {
  font-size: 6rem;
  transition: 0.5s;
}
.services-box:hover .icon :not(.icon-main .icon-arrow) {
  color: var(--main-color);
}
.services-box .icon a {
  display: inline-flex;
  background: var(--text-color);
  border-radius: 50%;
  padding: 1rem;
  transition: 0.5s;
}
.services-box .icon a .icon-arrow {
  font-size: 3rem;
  color: var(--bg-color);
  transform: rotate(225deg);
}
.services-box .icon a:hover .icon-arrow {
  transform: rotate(180deg);
}
.services-box h3 {
  font-size: 3rem;
  margin: 0.5rem 0 2rem;
  transition: 0.5s;
}
.services-box:hover h3 {
  color: var(--main-color);
}
.services-box p {
  font-size: 1.6rem;
}
</style>
