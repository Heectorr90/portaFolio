<script setup>
import NavBar from "./components/NavBar.vue";
import DatosPersonales from "./components/DatosPersonales.vue";
import ServiciosContainer from "./components/ServiciosContainer.vue";
import ResumenContainer from "./components/ResumenContainer.vue";
import ProyectosContainer from "./components/ProyectosContainer.vue";
import ContactoContainer from "./components/ContactoContainer.vue";
import { ref } from "vue";

const activeSection = ref("home");

const sections = [
  { id: "home", component: DatosPersonales },
  { id: "servicios", component: ServiciosContainer },
  { id: "resumen", component: ResumenContainer },
  { id: "proyectos", component: ProyectosContainer },
  { id: "contacto", component: ContactoContainer },
];
</script>

<template>
  <header class="header">
    <!-- Barra de Navegación -->
    <NavBar :active="activeSection" @navigate="(id) => (activeSection = id)" />
  </header>
  <main>
    <section
      v-for="s in sections"
      :key="s.id"
      :id="s.id"
      :class="[s.id, { active: activeSection === s.id }]"
    >
      <component :is="s.component" />
    </section>
  </main>
</template>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 10;
  width: 100%;
  padding: 2rem 9%;
  background: transparent;
  display: flex;
  justify-content: space-between;
  align-items: center;
  z-index: 100;
}

section {
  position: absolute;
  width: 100%;
  height: 100%;
  padding: 10rem 9% 2rem;
  background: var(--bg-color);
  visibility: hidden;
  opacity: 0;
  overflow: hidden;
}

section.active {
  visibility: visible;
  opacity: 1;
  overflow: auto;
}
.home {
  width: 100vw; /* Ocupa todo el ancho de la pantalla */
  max-width: 100vw; /* Evita que se limite por algún padre */
  overflow-x: hidden;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 9%;
  gap: 5rem;
}
</style>
