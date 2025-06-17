<script setup>
import IconCel from "./icons/IconCel.vue";

const contactItems = [
  {
    label: "Teléfono:",
    value: "+34 123 456 789",
    icon: IconCel,
  },
  {
    label: "Email:",
    value: "ejemplo@correo.com",
    icon: IconCel,
  },
  {
    label: "Lugar de Origen:",
    value: "Toluca, México",
    icon: IconCel,
  },
];
</script>

<template>
  <div class="contact-container">
    <div class="contact-box">
      <h2>Contacto</h2>
      <p class="desc">
        Si tienes alguna pregunta o deseas más información, no dudes en contactarme.
      </p>
      <div v-for="(item, index) in contactItems" :key="index" class="contact-detail">
        <component :is="item.icon" class="icon" />
        <div class="detail">
          <p>{{ item.label }}</p>
          <p>{{ item.value }}</p>
        </div>
      </div>
    </div>
    <div class="contact-box">
      <form action="">
        <h2 class="heading">Contáctame</h2>
        <div class="field-box">
          <input type="text" placeholder="Nombre" id="name" required />
          <input type="text" placeholder="Email" id="email" required />
          <input type="text" placeholder="Teléfono" id="phone" required />
          <input type="text" placeholder="Asunto" id="subject" required />
          <textarea placeholder="Escribe tu mensaje aquí..." id="message" required></textarea>
          <button type="submit" class="btn">Enviar</button>
        </div>
      </form>
    </div>
  </div>
</template>

<style scoped>
.contact-container {
  display: grid;
  grid-template-columns: 1fr 1.3fr;
  gap: 2rem;
}
.contact-container .contact-box:first-child {
  align-self: center;
}
.contact-box h2 {
  font-size: 4.5rem;
}
.contact-box p {
  font-size: 1.6rem;
}
.contact-box .desc {
  margin: 1.5rem 0 2.5rem;
}
.contact-detail {
  display: flex;
  align-items: center;
  margin: 2rem 0;
}
.contact-detail .icon {
  display: inline-flex;
  background: var(--second-bg-color);
  color: var(--main-color);
  font-size: 3rem;
  border-radius: 0.6rem;
  margin-right: 1.5rem;
}
.contact-detail .detail p:first-child {
  font-weight: 300;
  color: var(--main-color);
}

.contact-box from {
  background: var(--second-bg-color);
  padding: 2.5rem 3.5rem 3.5rem;
  border-radius: 1rem;
  text-align: center;
}
.contact-box .heading {
  font-size: 3.5rem;
}
.contact-box .field-box {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 2rem;
}
.contact-box .field-box input,
.contact-box .field-box textarea {
  padding: 1.5rem;
  background: var(--bg-color);
  border: 0.15rem solid var(--bg-color);
  border-radius: 0.6rem;
  font-size: 1.6rem;
  color: var(--text-color);
}
.contact-box .field-box textarea {
  grid-column: 1 / -1;
  height: 26rem;
  resize: none;
}
.contact-box .field-box input:focus,
.contact-box .field-box textarea:focus {
  border-color: var(--main-color);
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
</style>
