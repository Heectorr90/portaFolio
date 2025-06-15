<script setup>
import NavBar from "./components/navBar.vue";
import DatosPersonales from "./components/DatosPersonales.vue";
</script>

<template>
  <header class="header">
    <!-- Barra de Navegación -->
    <NavBar />
  </header>
  <main>
    <section class="home" id="home"><DatosPersonales /></section>
    <section id="educacion"><h2>Educacion - Cursos</h2></section>
    <section id="experiencia"><h2>Experiencia</h2></section>
    <section id="proyectos"><h2>Proyectos</h2></section>
    <section id="habilidades"><h2>Habilidades</h2></section>
    <section id="intereses"><h2>Intereses</h2></section>
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
  min-height: 100vh;
  padding: 10rem 9% 2rem;
}

.home {
  display: flex;
  align-items: center;
  padding: 0 9%;
  background: url("../assets/home.png") no-repeat;
  background-size: cover;
  background-position: center;
}
</style>
