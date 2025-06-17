<script setup>
import IconGitHub from "@/components/icons/IconGitHub.vue";
import IconFlechaAtras from "@/components/icons/servicios/IconFlechaAtras.vue";
import IconArrowChica from "@/components/icons/IconArrowChica.vue";

import { ref } from "vue";

const props = defineProps({
  project: {
    type: Object,
    required: true,
  },
  number: {
    type: String,
    required: true,
  },
});

const currentImage = ref(0);

function nextImage() {
  currentImage.value = (currentImage.value + 1) % props.project.images.length;
}

function prevImage() {
  currentImage.value =
    (currentImage.value - 1 + props.project.images.length) % props.project.images.length;
}
</script>

<template>
  <div class="portfolio-container">
    <!-- Detalles -->
    <div class="portfolio-box">
      <div class="portfolio-detail active">
        <p class="numb">{{ number }}</p>
        <h3>{{ project.title }}</h3>
        <p>{{ project.description }}</p>
        <div class="tech">
          <p>{{ project.tech.join(", ") }}</p>
        </div>
        <div class="live-github">
          <a class="iconos" :href="project.liveUrl" target="_blank">
            <IconFlechaAtras class="icon" />
            <span>Ver en vivo</span>
          </a>
          <a class="iconos" :href="project.githubUrl" target="_blank">
            <IconGitHub class="icon" />
            <span>Ver en GitHub</span>
          </a>
        </div>
      </div>
    </div>

    <!-- Carrusel -->
    <div class="portfolio-box">
      <div class="portfolio-carousel">
        <div class="img-slide">
          <div
            class="img-item"
            v-for="(img, index) in project.images"
            :key="index"
            v-show="currentImage === index"
          >
            <img :src="img" />
          </div>
        </div>
        <div class="navegation">
          <button class="prev" @click="prevImage"><IconArrowChica /></button>
          <button class="next" @click="nextImage"><IconArrowChica /></button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.portfolio-container {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 3rem;
}
.portfolio-detail {
  display: none;
}
.portfolio-detail.active {
  display: block;
}
.portfolio-box .numb {
  font-size: 8rem;
  -webkit-text-stroke: 0.07rem var(--main-color);
  color: transparent;
  line-height: 1;
}
.portfolio-box h3 {
  font-size: 3.5rem;
  margin: 0.8rem 0 2rem;
}
.portfolio-box p {
  font-size: 1.6rem;
}
.portfolio-box .tech {
  margin: 2rem 0;
  color: var(--main-color);
  border-bottom: 0.1rem solid var(--text-color);
  padding-bottom: 2rem;
}
.portfolio-box .live-github .iconos {
  position: relative;
  display: inline-flex;
  padding: 1.3rem;
  font-size: 3rem;
  color: var(--text-color);
  border-radius: 50%;
  background: var(--second-bg-color);
  transition: 0.5s;
}
.portfolio-box .live-github .iconos:hover {
  color: var(--main-color);
}
.portfolio-box .live-github .iconos:first-child {
  margin-right: 1.5rem;
}
.portfolio-box .live-github .iconos:first-child .icon {
  transform: rotate(135deg);
}
.portfolio-box .live-github .iconos span {
  position: absolute;
  top: -60%;
  left: 50%;
  transform: translateX(-50%) scale(0.9);
  font-size: 1.6rem;
  white-space: nowrap;
  padding: 0.5rem 1rem;
  border-radius: 0.6rem;
  pointer-events: none;
  background: var(--text-color);
  color: var(--bg-color);
  opacity: 0;
  scale: 0.9;
}
.portfolio-box .live-github .iconos:hover span {
  top: -70%;
  opacity: 1;
  transform: translateX(-50%) scale(1);
}
.portfolio-box .portfolio-carousel {
  width: 100%;
  height: 45rem;
  border-radius: 1rem;
}
.portfolio-carousel .img-slide {
  display: grid;
  grid-auto-flow: column;
  grid-auto-columns: 100%;
  gap: 2rem;
  height: inherit;
  transition: 0.5s;
}
.portfolio-carousel .img-item {
  height: inherit;
}
.portfolio-carousel .img-item img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 1rem;
}
.portfolio-box .navegation {
  text-align: right;
  margin-top: 2rem;
}
.portfolio-box .navegation button {
  display: inline-flex;
  padding: 0.5rem;
  background: var(--second-bg-color);
  border: 0.2rem solid var(--main-color);
  border-radius: 0.6rem;
  font-size: 4rem;
  color: var(--main-color);
  cursor: pointer;
}
.portfolio-box .navegation .prev {
  transform: rotate(180deg);
}
.portfolio-box .navegation .next {
  margin-left: 1.5rem;
}
</style>
