<template>
  <div class="slider-controls d-flex align-items-center">
    <img :src="prevIcon" alt="Anterior" @click="$emit('prev')" class="control-icon me-2" />
    <img :src="nextIcon" alt="Siguiente" @click="$emit('next')" class="control-icon me-2" />
    <img :src="pauseIcon" alt="Pausa" @click="$emit('pause')" class="control-icon" />
  </div>
</template>

<script setup>
defineEmits(['prev','next','pause'])
import prevIcon from '@/assets/left.svg'
import nextIcon from '@/assets/right.svg'
import pauseIcon from '@/assets/pause.svg'
</script>

<style scoped>
.slider-controls {
  position: absolute;
  bottom: 2rem;
  left: 2rem;
  z-index: 3;
}
.control-icon {
  width: 40px;
  height: 40px;
  cursor: pointer;
  transition: transform 0.1s;
}
.control-icon:hover {
  transform: scale(1.1);
}
.control-icon:active {
  transform: scale(0.95);
}
</style>
