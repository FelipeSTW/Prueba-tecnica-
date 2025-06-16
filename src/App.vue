<template>
  <NavBar />
  <div class="banner-completo">
    <Ficha />
    <HeroBanner />
  </div>


  <router-view />
</template>

<script setup>
import NavBar from "./components/NavBar.vue";
import Ficha from "./components/Ficha.vue";
import HeroBanner from "./components/HeroBanner.vue";
</script>

<style>
.banner-completo {
  max-height: 584px;
  position:relative;
}
</style>
