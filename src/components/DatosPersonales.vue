<script setup>
import IconFacebook from "./icons/IconFacebook.vue";
import IconInstagram from "./icons/IconInstagram.vue";
import IconLinkedin from "./icons/IconLinkedin.vue";
const title = "Héctor Ramírez";
const profession = "Desarrollador Web Full Stack";
const description =
  "Apasionado por crear soluciones innovadoras y eficientes. Con experiencia en el desarrollo de aplicaciones web modernas y escalables, utilizando tecnologías como Vue.js, Node.js y bases de datos relacionales y no relacionales.";
const redesSociales = [
  {
    name: "Facebook",
    url: "https://facebook.com/hector",
    icon: IconFacebook,
  },
  {
    name: "Instagram",
    url: "https://instagram.com/hector",
    icon: IconInstagram,
  },
  {
    name: "LinkedIn",
    url: "https://www.linkedin.com/in/hector",
    icon: IconLinkedin,
  },
];
</script>

<template>
  <div class="home-content">
    <h1>
      Hola soy <span>{{ title }}</span>
    </h1>
    <div class="text-animate">
      <h3>{{ profession }}</h3>
    </div>
    <p>{{ description }}</p>
    <br />
    <div class="btn-box">
      <a href="#" class="btn"> CV </a>
      <div class="home-sci">
        <a
          v-for="red in redesSociales"
          :key="red.name"
          :href="red.url"
          target="_blank"
          rel="noopener noreferrer"
        >
          <component :is="red.icon" class="w-6 h-6" />
        </a>
      </div>
    </div>
  </div>
  <div class="home-img">
    <div class="img-box">
      <div class="img-item">
        <img src="../assets/img/home-foto.png" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.home-content {
  flex: 1.2;
}
.home-content h1 {
  font-size: 5.6rem;
  font-weight: 700;
  line-height: 1.3;
}
.home-content .text-animate {
  position: relative;
  width: 32.8rem;
}
.home-content .text-animate h3 {
  font-size: 3.2rem;
  font-weight: 700;
  color: transparent;
  -webkit-text-stroke: 0.7px var(--main-color);
}
.home-content p {
  font-size: 1.6rem;
  line-height: 2.4rem 0 4rem;
}
.btn-box {
  display: flex;
  justify-content: space-between;
  width: 34.5rem;
  height: 5rem;
}
.btn {
  position: relative;
  display: inline-flex;
  justify-content: center;
  align-items: center;
  width: 15rem;
  height: 100%;
  background: var(--main-color);
  border: 0.2rem solid var(--main-color);
  border-radius: 0.8rem;
  font-size: 1.8rem;
  font-weight: 600;
  letter-spacing: 0.1rem;
  color: var(--bg-color);
  z-index: 1;
  overflow: hidden;
  transition: 0.5s;
}

.btn:hover {
  color: var(--main-color);
  background: transparent;
}
.btn::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 0;
  height: 100%;
  background: var(--bg-color);
  z-index: -1;
  transition: 0.5s;
}
.btn-box .btn:hover::before {
  width: 100%;
}
.home-sci {
  display: flex;
  gap: 1rem;
  align-items: center;
  margin-left: 2rem;
  width: 170px;
  display: flex;
  justify-content: space-between;
}

.home-sci a {
  position: relative;
  display: inline-flex;
  justify-content: center;
  align-items: center;
  width: 40px;
  height: 40px;
  background: transparent;
  border: 0.2rem solid var(--main-color);
  border-radius: 50%;
  color: var(--main-color);
  font-size: 20px;
  z-index: 1;
  overflow: hidden;
}
.home-sci a:hover {
  color: var(--bg-color);
  background: transparent;
}
.home-sci a::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 0;
  height: 100%;
  background: var(--main-color);
  z-index: -1;
  transition: 0.5s;
}
.home-sci a:hover::before {
  width: 100%;
}

.home-img .img-box {
  flex: 0.8;
  position: relative;
  width: 32vw;
  height: 32vw;
  border-radius: 50%;
  padding: 0.5rem;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}
.home-img .img-box::before,
.home-img .img-box::after {
  content: "";
  position: absolute;
  width: 50rem;
  height: 50rem;
  background: conic-gradient(transparent, transparent, transparent, var(--main-color));
  transform: rotate(0deg);
  animation: rotate-border 10s linear infinite;
}
.home-img .img-box::after {
  animation-delay: -5s;
}
@keyframes rotate-border {
  100% {
    transform: rotate(360deg);
  }
}
.home-img .img-box .img-item {
  position: relative;
  width: 100%;
  height: 100%;
  background-color: var(--bg-color);
  border-radius: 50%;
  border: 0.01rem solid var(--bg-color);
  display: flex;
  justify-content: center;
  z-index: 1;
  overflow: hidden;
}
.home-img .img-box .img-item img {
  position: absolute;
  top: 3rem;
  display: block;
  width: 85%;
  object-fit: cover;
  mix-blend-mode: lighten;
}
</style>
