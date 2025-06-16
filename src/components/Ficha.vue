<template>
  <section class="ficha-banner">
    <div class="container d-flex align-items-center py-2">
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
  background: linear-gradient(90deg, #242a8c 0%, #0e0d8a 100%);
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
</style>
