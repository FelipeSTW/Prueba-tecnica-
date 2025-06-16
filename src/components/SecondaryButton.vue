<template>
  <button class="btn btn-secondary-custom" @click="$emit('click')">
    <slot />
  </button>
</template>

<script setup>
// SecondaryButton: estilo outline para "Nuestras tarifas"
</script>

<style scoped>
.btn-secondary-custom {
  background-color: transparent;
  color: #ffffff;
  text-transform: uppercase;
  font-weight: 500;
  padding: 0.75rem 1.75rem;
  border: 2px solid #ffffff;
  border-radius: 6px;
  transition: background-color 0.2s, color 0.2s;
  white-space: nowrap;
  min-width: 180px;
}
.btn-secondary-custom:hover {
  background-color: rgba(255,255,255,0.1);
  color: #00e09b;
}
</style>