<template>
  <section class="ficha-banner">
    <div class="container d-flex align-items-center content-ficha">
      <img :src="truckIcon" alt="Camión" class="icon-truck me-2" />

      <span class="ficha-text">
        ¡Contrata hoy y obtén <strong>los mejores beneficios</strong>
      </span>
    </div>
  </section>
</template>

<script setup>
import truckIcon from "@/assets/truck.png";
</script>

<style scoped>
.ficha-banner {
  background: rgba(26, 30, 137, 0.5);
  font-family: 'Nunito Sans', sans-serif;
  font-weight: 700;       
  font-size: 12px;         
  line-height: 24px;       
  letter-spacing: 0.4px;   
  text-align: center;
  height: 64px;display: flex;
  align-items: center;
  position: absolute;
  width: 100%;
  z-index: 99;
}

.icon-truck {
  width: 24px;
  height: 24px;
  object-fit: contain;
}

.ficha-text {
  color: #ffffff;
  font-size: 1rem;
  font-weight: 500;
}

.content-ficha {
  justify-content: center;
}

@media (max-width: 768px) {
  .ficha-banner {
    height: 48px;
  }
}
</style>
