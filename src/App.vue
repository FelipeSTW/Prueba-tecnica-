<template>
  <NavBar />
  <Ficha />
  <HeroBanner />

  <router-view />
</template>

<script setup>
import NavBar from "./components/NavBar.vue";
import Ficha from "./components/Ficha.vue";
import HeroBanner from "./components/HeroBanner.vue";
</script>
