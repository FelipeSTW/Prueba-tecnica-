<template>
  <nav class="navbar-custom">
    <div class="container-fluid">
      <div class="nav-wrapper">
        <!-- Logo -->
        <div class="nav-brand">
          <router-link to="/" class="d-flex align-items-center text-decoration-none">
            <img :src="logo" alt="Pago de Banco de Chile" class="logo" />
          </router-link>
        </div>

        <!-- Desktop/Tablet: Links al centro -->
        <div class="nav-links d-none d-md-block">
          <ul class="mb-0">
            <li><a href="#">Productos y tarifas</a></li>
            <li><a href="#">Cómo contratar</a></li>
            <li><a href="#">Beneficios</a></li>
          </ul>
        </div>

        <!-- Desktop/Tablet: Botón a la derecha -->
        <div class="nav-cta d-none d-md-block">
          <button class="btn btn-cta">QUIERO CONTRATAR</button>
        </div>

        <!-- Mobile: Botón CTA + Hamburger -->
        <div class="mobile-nav d-md-none d-flex align-items-center gap-2">
          <button class="btn btn-cta btn-cta-mobile">CONTRATAR</button>
          <button 
            class="btn-hamburger" 
            @click="toggleMenu"
            :class="{ active: isMenuOpen }"
          >
            <span></span>
            <span></span>
            <span></span>
          </button>
        </div>
      </div>
    </div>

    <!-- Mobile Sidebar Menu -->
    <div class="mobile-menu" :class="{ active: isMenuOpen }">
      <div class="mobile-menu-content">
        <ul class="mobile-nav-links">
          <li><a href="#" @click="closeMenu">Productos y tarifas</a></li>
          <li><a href="#" @click="closeMenu">Cómo contratar</a></li>
          <li><a href="#" @click="closeMenu">Beneficios</a></li>
        </ul>
      </div>
    </div>

    <!-- Overlay -->
    <div 
      class="mobile-overlay" 
      :class="{ active: isMenuOpen }" 
      @click="closeMenu"
    ></div>
  </nav>
</template>

<script setup>
import { ref } from 'vue'
import logo from "@/assets/logo.png"

const isMenuOpen = ref(false)

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const closeMenu = () => {
  isMenuOpen.value = false
}
</script>

<style scoped>
/* Navbar general */
.navbar-custom {
  background-color: #0e0d8a;
  position: relative;
  z-index: 1000;
}

/* Wrapper principal */
.nav-wrapper {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 72px;
  padding: 0 1rem;
}

/* Logo */
.nav-brand .logo {
  height: 21px;
  width: auto;
}

/* Desktop/Tablet navigation */
.nav-links {
  display: flex;
  align-items: center;
}

.nav-links ul {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
  gap: 2rem;
}

.nav-links a {
  color: #ffffff;
  text-transform: uppercase;
  font-weight: 500;
  font-size: 0.875rem;
  text-decoration: none;
  transition: color 0.2s;
}

.nav-links a:hover {
  color: #00e09b;
}

/* Botón CTA */
.btn-cta {
  background-color: #00DBBC;
  color: #0e0d8a;
  text-transform: uppercase;
  font-weight: 600;
  font-size: 0.75rem;
  padding: 8px 16px;
  border: none;
  border-radius: 6px;
  white-space: nowrap;
  transition: all 0.2s;
  min-width: 170px;
}

.btn-cta:hover {
  background-color: #00c88d;
  transform: translateY(-1px);
}

/* Botón CTA Mobile */
.btn-cta-mobile {
  min-width: 100px;
  font-size: 0.65rem;
  padding: 6px 12px;
}

/* Hamburger button */
.btn-hamburger {
  background: none;
  border: none;
  width: 30px;
  height: 24px;
  position: relative;
  cursor: pointer;
  padding: 0;
}

.btn-hamburger span {
  display: block;
  height: 3px;
  width: 100%;
  background-color: #ffffff;
  margin: 5px 0;
  transition: all 0.3s ease;
  transform-origin: center;
}

.btn-hamburger.active span:nth-child(1) {
  transform: rotate(45deg) translate(6px, 6px);
}

.btn-hamburger.active span:nth-child(2) {
  opacity: 0;
}

.btn-hamburger.active span:nth-child(3) {
  transform: rotate(-45deg) translate(6px, -6px);
}

/* Mobile Menu Sidebar */
.mobile-menu {
  position: fixed;
  top: 0;
  right: -300px;
  width: 280px;
  height: 100vh;
  background-color: #0e0d8a;
  transition: right 0.3s ease;
  z-index: 1001;
  padding-top: 80px;
}

.mobile-menu.active {
  right: 0;
}

.mobile-menu-content {
  padding: 2rem 1.5rem;
}

.mobile-nav-links {
  list-style: none;
  padding: 0;
  margin: 0;
}

.mobile-nav-links li {
  margin-bottom: 1.5rem;
}

.mobile-nav-links a {
  color: #ffffff;
  text-transform: uppercase;
  font-weight: 500;
  font-size: 1rem;
  text-decoration: none;
  display: block;
  padding: 0.5rem 0;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  transition: color 0.2s;
}

.mobile-nav-links a:hover {
  color: #00e09b;
}

/* Mobile Overlay */
.mobile-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 999;
  opacity: 0;
  visibility: hidden;
  transition: all 0.3s ease;
}

.mobile-overlay.active {
  opacity: 1;
  visibility: visible;
}

/* Responsive adjustments */
@media (min-width: 768px) and (max-width: 1199px) {
  .nav-wrapper {
    padding: 0 2rem;
  }
  
  .nav-links a {
    font-size: 0.8rem;
    gap: 1.5rem;
  }
  
  .btn-cta {
    min-width: 150px;
    font-size: 0.7rem;
  }
}

@media (min-width: 1200px) {
  .nav-wrapper {
    padding: 0 75px;
    max-width: 1440px;
    margin: 0 auto;
  }
}

@media (max-width: 767px) {
  .nav-wrapper {
    padding: 0 1rem;
  }
}
</style>