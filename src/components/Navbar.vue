<template>
  <nav class="navbar-custom">
    <!-- DIV PRINCIPAL -->
    <div class="container nav-wrapper">
      
      <!-- SUB DIV 1: Marca -->
      <div class="nav-brand">
        <router-link to="/" class="d-flex align-items-center text-decoration-none">
          <img :src="logo" alt="Pago de Banco de Chile" class="logo me-2" />
         
        </router-link>
      </div>

      <!-- SUB DIV 2: Enlaces -->
      <div class="nav-links">
        <ul>
          <li><a href="#">Productos y tarifas</a></li>
          <li><a href="#">Cómo contratar</a></li>
          <li><a href="#">Beneficios</a></li>
        </ul>
      </div>

      <!-- SUB DIV 3: Botón CTA -->
      <div class="nav-cta">
        <button class="btn btn-cta">QUIERO CONTRATAR</button>
      </div>

    </div>
  </nav>
</template>

<script>
import logo from '@/assets/logo.png'

export default {
  name: 'Navbar',
  data() {
    return { logo }
  }
}
</script>

<style scoped>
/* NAVBAR */
.navbar-custom {
  background-color: #0e0d8a;
  border-bottom-left-radius: 1rem;
  border-bottom-right-radius: 1rem;
}

/* WRAPPER */
.nav-wrapper {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1rem 0;
}

/* LOGO + TEXTO */
.nav-brand .logo {
  height: 40px;
  width: auto;
}
.brand-text {
  font-size: 1.125rem;
  color: #fff;
  user-select: none;
}

/* LINKS */
.nav-links ul {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
  gap: 2rem;
}
.nav-links a {
  color: #fff;
  text-transform: uppercase;
  font-weight: 500;
  text-decoration: none;
  transition: color 0.2s;
}
.nav-links a:hover {
  color: #00e09b;
}

/* BOTÓN CTA */
.btn-cta {
  background-color: #00e09b;
  color: #0e0d8a;
  text-transform: uppercase;
  font-weight: 600;
  padding: 0.5rem 1.5rem;
  border: none;
  border-radius: 0.375rem;
  transition: background-color 0.2s, transform 0.1s;
}
.btn-cta:hover {
  background-color: #00c88d;
  transform: translateY(-1px);
}
.btn-cta:active {
  transform: translateY(0);
}
</style>
