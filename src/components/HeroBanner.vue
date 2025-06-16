<template>
  <section class="hero-banner position-relative">
    <div class="hero-bg"></div>

    <!-- Carousel wrapper -->
    <Carousel 
      :autoplay="3000" 
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
                
                <div class="hero-buttons d-flex flex-column flex-sm-row gap-3">
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
            @prev="$refs.carousel?.prev()"
            @next="$refs.carousel?.next()"
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
    title: "Segundo slide - Texto diferente ",
    titleBold: "con otros beneficios*",
    ctaText: "Quiero contratar",
    secondaryText: "Nuestras tarifas", 
    personImg: personaImg,
    phoneImg: celularImg
  }
])

const isAutoplayPaused = ref(false)

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
  isAutoplayPaused.value = !isAutoplayPaused.value
  console.log('Autoplay toggled:', !isAutoplayPaused.value)
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
  height: 400px;
  margin: 0 auto;
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
  bottom: 0;
  left: 0;
  width: 70%;
  height: auto;
  z-index: 1;
}

.celular-img {
  position: absolute;
  top: 15%;
  right: 10%;
  width: 45%;
  height: auto;
  transform: rotate(-10deg);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
  z-index: 2;
}

/* Controles del carousel */
.carousel-controls {
  position: absolute;
  bottom: 2rem;
  left: 2rem;
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
    height: 350px;
  }
  
  .hero-buttons {
    flex-direction: row;
    gap: 1rem;
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
    width: 40%;
    top: 10%;
  }
  
  .persona-img {
    width: 60%;
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