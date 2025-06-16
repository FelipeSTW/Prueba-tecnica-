<template>
  <section class="hero-banner position-relative">

    <div class="hero-bg"></div>

    <div class="container hero-content d-flex align-items-center py-5">

      <div class="hero-text flex-shrink-0">
        <h1 class="display-6 mb-4">
          Hazte cliente empresa del <br>
          Banco de Chile y <strong>obtén tu producto a costo $0*</strong>
        </h1>
        <div class="d-flex gap-3">
          <CtaButton @click="onContratar">Quiero contratar</CtaButton>
          <SecondaryButton @click="onTarifas">Nuestras tarifas</SecondaryButton>
        </div>
      </div>


      <div class="hero-images ms-auto position-relative">
        <img :src="backgroundShapeImg" alt="backgroundshape" class="shape-img" />
        <img :src="personaImg" alt="Persona" class="persona-img" />
        <img :src="celularImg" alt="Celular" class="celular-img" />
        <!-- Controles del slider -->
        <SliderControls
          @prev="onPrev"
          @next="onNext"
          @pause="onPause"
        />
      </div>
    </div>
  </section>
</template>

<script setup>
import CtaButton from '@/components/CtaButton.vue'
import SecondaryButton from '@/components/SecondaryButton.vue'
import backgroundShapeImg from '@/assets/backgroundshape.png'
import SliderControls from '@/components/SliderControls.vue'
import personaImg from '@/assets/persona.png'
import celularImg from '@/assets/celular.png'
import heroBg from '@/assets/hero_bg.png'

const onContratar = () => {

}
const onTarifas = () => {

}


const onPrev = () => {
  console.log('Prev slide')
}
const onNext = () => {
  console.log('Next slide')
}
const onPause = () => {
  console.log('Pause slider')
}

</script>


<style scoped>
.hero-banner {
  overflow: hidden;
  border-bottom-left-radius: 1rem;
  border-bottom-right-radius: 1rem;
}

.hero-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, #242a8c 0%, #0e0d8a 100%),
    url('@/assets/hero_bg.png') center/cover no-repeat;
  z-index: -2;
}

.hero-bg::after {
  content: '';
  position: absolute;
  inset: 0;
  background: none;
}

.hero-content {
  position: relative;
}
h1.display-6.mb-4 {
      font-family: 'Nunito Sans', sans-serif;
      width: 470px;
      height: 144px;
      font-size: 40px;
      
      
}

.hero-text h1 {
  color: #ffffff;
  font-weight: 400;

}

.hero-images {
  width: 50%;
  min-width: 300px;
  height: auto;
}

.shape-img {
  position: absolute;
  top: 10%;
  left: 0;
  width: 120%;
  height: auto;
}

.persona-img {
  position: relative;
  width: 100%;
  height: auto;
  z-index: 1;
}

.celular-img {
  position: absolute;
  top: 15%;
  left: 20%;
  width: 60%;
  height: auto;
  transform: rotate(-10deg);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
  z-index: 2;
}
.btn-cta {
  font-family: 'Nunito Sans', sans-serif;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 70px;
  height: 40px;
  padding: 8px 16px;
  border-radius: 260px;
  margin-right: 12px;
  white-space: nowrap;

  /* Colores y tipografía */
  background-color: #00DBBC;
  color: #0e0d8a;
  text-transform: uppercase;
  font-weight: 600;

  /* Transiciones */
  transition: background-color 0.2s, transform 0.1s;
}

.btn-cta:hover {
  background-color: #00DBBC;
  transform: translateY(-1px);
}
.btn-cta:active {
  transform: translateY(0);
}
</style>