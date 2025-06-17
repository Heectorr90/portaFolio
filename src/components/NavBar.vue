<script setup>
import IconMenu from "./icons/IconMenu.vue";
import { defineProps, defineEmits } from "vue";
const props = defineProps({ active: String });
const emit = defineEmits(["navigate"]);

const navegacion = [
  { id: "home", name: "Home" },
  { id: "servicios", name: "Servicios" },
  { id: "resumen", name: "Resumen" },
  { id: "proyectos", name: "Proyectos" },
  { id: "contacto", name: "Contacto" },
];

function navegar(id) {
  emit("navigate", id);
}
</script>

<template>
  <a href="#" class="logo" @click.prevent="navegar('home')">Hector.</a>
  <div class="menu-icon"><IconMenu /></div>
  <nav class="navbar">
    <a
      v-for="nav in navegacion"
      :key="nav.id"
      href="#"
      :class="{ active: nav.id === active }"
      @click.prevent="navegar(nav.id)"
    >
      {{ nav.name }}
    </a>
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
