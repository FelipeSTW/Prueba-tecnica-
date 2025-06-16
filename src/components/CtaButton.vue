<template>
  <button class="btn btn-cta" @click="$emit('click')">
    <slot />
  </button>
</template>

<script setup>
// CtaButton: botón principal reutilizable (turquesa)
</script>

<style scoped>
.btn-cta {
  background-color: #00e09b;
  color: #0e0d8a;
  text-transform: uppercase;
  font-weight: 600;
  padding: 0.75rem 1.75rem;
  border: none;
  border-radius: 32px;
  transition: background-color 0.2s, transform 0.1s;
  white-space: nowrap;
  min-width: 180px;
  min-width: fit-content;
}
.btn-cta:hover {
  background-color: #00c88d;
  transform: translateY(-1px);
}
.btn-cta:active {
  transform: translateY(0);
}
</style>