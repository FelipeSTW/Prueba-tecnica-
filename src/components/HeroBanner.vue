<template>
  <section class="hero-banner position-relative">
    <div class="hero-bg"></div>

    <!-- Carousel wrapper -->
    <Carousel 
      ref="carousel"
      :autoplay="isAutoplayActive ? 3000 : 0" 
      :wrap-around="true" 
      :transition="500"
      @slide-start="onSlideStart"
    >
      <Slide v-for="(slide, index) in slides" :key="index">
        <div class="container-fluid">
          <div class="hero-content row align-items-center py-5">
            
            <!-- Texto - Desktop/Tablet: col-6, Mobile: col-12 -->
            <div class="col-12 col-md-6 hero-text-col">
              <div class="hero-text">
                <h1 class="hero-title mb-4">
                  {{ slide.title }} <strong>{{ slide.titleBold }}</strong>
                </h1>
                
                <div class="hero-buttons d-flex gap-3">
                  <CtaButton @click="onContratar">{{ slide.ctaText }}</CtaButton>
                  <SecondaryButton @click="onTarifas">{{ slide.secondaryText }}</SecondaryButton>
                </div>
              </div>
            </div>

            <!-- Imágenes - Desktop/Tablet: col-6, Mobile: col-12 -->
            <div class="col-12 col-md-6 hero-images-col">
              <div class="hero-images position-relative">
                <img :src="backgroundShapeImg" alt="backgroundshape" class="shape-img" />
                <img :src="slide.personImg" alt="Persona" class="persona-img" />
                <img :src="slide.phoneImg" alt="Celular" class="celular-img" />
              </div>
            </div>

          </div>
        </div>
      </Slide>

      <!-- Controles del carousel -->
      <template #addons>
        <div class="carousel-controls">
          <SliderControls
            @prev="carousel?.prev()"
            @next="carousel?.next()"
            @pause="toggleAutoplay"
          />
        </div>
      </template>
    </Carousel>
  </section>
</template>

<script setup>
import { ref } from 'vue'
import { Carousel, Slide } from 'vue3-carousel'
import CtaButton from '@/components/CtaButton.vue'
import SecondaryButton from '@/components/SecondaryButton.vue'
import SliderControls from '@/components/SliderControls.vue'
import backgroundShapeImg from '@/assets/backgroundshape.png'
import personaImg from '@/assets/persona.png'
import celularImg from '@/assets/celular.png'

const isAutoplayActive = ref(true)
const carousel = ref(null)

// Datos del carousel (puedes agregar más slides aquí)
const slides = ref([
  {
    title: "Hazte cliente empresa del Banco de Chile y ",
    titleBold: "obtén tu producto a costo $0*",
    ctaText: "Quiero contratar",
    secondaryText: "Nuestras tarifas",
    personImg: personaImg,
    phoneImg: celularImg
  },
  // Agregar más slides aquí si necesitas
  {
    title: "Hazte cliente empresa del Banco de Chile  ",
    titleBold: "y obten tu producto a costo 0*",
    ctaText: "Quiero contratar",
    secondaryText: "Nuestras tarifas", 
    personImg: personaImg,
    phoneImg: celularImg
  }
])

const onContratar = () => {
  console.log('Contratar clicked')
}

const onTarifas = () => {
  console.log('Tarifas clicked')
}

const onSlideStart = (slideIndex) => {
  console.log('Slide changed to:', slideIndex)
}

const toggleAutoplay = () => {
  isAutoplayActive.value = !isAutoplayActive.value
  console.log('Autoplay toggled:', isAutoplayActive.value)
}
</script>

<style scoped>
.hero-banner {
  overflow: hidden;
  border-bottom-left-radius: 1rem;
  border-bottom-right-radius: 1rem;
  min-height: 500px;
}

.hero-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, #242a8c 0%, #0e0d8a 100%),
    url('@/assets/hero_bg.png') center/cover no-repeat;
  z-index: -1;
}

.hero-content {
  min-height: 500px;
  padding: 2rem 1rem;
}

/* Texto */
.hero-text-col {
  display: flex;
  align-items: center;
  z-index: 2;
}

.hero-title {
  color: #ffffff;
  font-weight: 400;
  font-size: 2.5rem;
  line-height: 1.2;
  margin-bottom: 2rem;
}

.hero-title strong {
  font-weight: 700;
}

.hero-buttons {
  max-width: 400px;
  flex-direction: row;
}

/* Imágenes */
.hero-images-col {
  display: flex;
  justify-content: center;
  align-items: center;
}

.hero-images {
  width: 100%;
  max-width: 500px;
  height: 450px;
  margin: 0 auto;
  overflow: hidden;
}

.shape-img {
  position: absolute;
  top: 10%;
  left: -10%;
  width: 120%;
  height: auto;
  z-index: 0;
}

.persona-img {
  position: absolute;
  bottom: -115px;
  left: 0;
  width: 67%;
  height: auto;
  z-index: 1;
  object-fit: cover;
  object-position: top;
}

.celular-img {
  position: absolute;
  top: -2%;
  right: -7%;
  width: 84%;
  height: auto;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
  z-index: 2;
}

/* Controles del carousel */
.carousel-controls {
  position: absolute;
  bottom: 2rem;
  left: 16rem;
  z-index: 10;
}

/* Responsive Design */

/* Tablet */
@media (min-width: 768px) and (max-width: 1199px) {
  .hero-content {
    padding: 1.5rem;
  }
  
  .hero-title {
    font-size: 2rem;
  }
  
  .hero-images {
    max-width: 400px;
    height: 380px;
  }
  
  .persona-img {
    width: 66%;
    bottom: -90px;
  }
  
  .celular-img {
    width: 85%;
    top: 5%;
    right: -5%;
  }
  
  .hero-buttons {
    flex-direction: column;
    gap: 1rem;
    max-width: 240px;
  }
}

/* Desktop */
@media (min-width: 1200px) {
  .hero-content {
    padding: 3rem 2rem;
    max-width: 1440px;
    margin: 0 auto;
  }
  
  .hero-title {
    font-size: 2.5rem;
    max-width: 470px;
  }
  
  .hero-images {
    max-width: 600px;
    height: 450px;
  }
  
  .hero-buttons {
    flex-direction: row;
    gap: 1.5rem;
  }
}

/* Mobile */
@media (max-width: 767px) {
  .hero-banner {
    min-height: auto;
  }
  
  .hero-content {
    min-height: auto;
    padding: 1rem;
    text-align: center;
  }
  
  .hero-text-col {
    order: 1;
    margin-bottom: 2rem;
  }
  
  .hero-images-col {
    order: 2;
  }
  
  .hero-title {
    font-size: 1.75rem;
    margin-bottom: 1.5rem;
  }
  
  .hero-buttons {
    flex-direction: column;
    gap: 1rem;
    width: 100%;
    max-width: 280px;
    margin: 0 auto;
  }
  
  .hero-images {
    max-width: 300px;
    height: 250px;
  }
  
  .celular-img {
    width: 75%;
    top: 10%;
  }
  
  .persona-img {
    width: 65%;
    bottom: -80px;
  }
  
  .carousel-controls {
    bottom: 1rem;
    left: 1rem;
  }
}

/* Carousel customization */
:deep(.carousel__viewport) {
  height: 100%;
}

:deep(.carousel__track) {
  height: 100%;
}

:deep(.carousel__slide) {
  height: 100%;
}
</style>