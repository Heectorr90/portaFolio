<script setup>
import IconMenu from "./icons/IconMenu.vue";
import { ref } from "vue";
const navegacion = ref([
  { id: 1, name: "Educacion", href: "#educacion" },
  { id: 2, name: "Experiencia", href: "#experiencia" },
  { id: 3, name: "Proyectos", href: "#proyectos" },
  { id: 4, name: "Habilidades", href: "#habilidades" },
]);
</script>

<template>
  <a href="#" class="logo">Hector.</a>
  <div class="menu-icon">
    <IconMenu />
  </div>
  <nav class="navbar">
    <a href="#" class="active">Home</a>
    <a v-for="nav in navegacion" :key="nav.id" :href="nav.href" class="navbar item">{{
      nav.name
    }}</a>
  </nav>
</template>

<style scoped>
.logo {
  color: var(--text-color);
  font-size: 2.5rem;
  font-weight: 600;
}
.navbar a {
  color: var(--text-color);
  font-size: 1.7rem;
  font-weight: 500;
  margin-left: 3.5rem;
  transition: 0.3s;
}
.navbar a:hover,
.navbar a.active {
  color: var(--main-color);
}
.navbar {
  display: flex;
  align-items: center;
  justify-content: center;
}

.menu-icon {
  font-size: 3.6rem;
  color: var(--text-color);
  cursor: pointer;
  display: none;
}
</style>
