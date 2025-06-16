<template>
  <nav class="navbar-custom">
    <!-- DIV PRINCIPAL -->
    <div class="container nav-wrapper">
      <!-- SUB DIV 1: Marca -->
      <div class="nav-brand">
        <router-link
          to="/"
          class="d-flex align-items-center text-decoration-none"
        >
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
import logo from "@/assets/logo.png";

export default {
  name: "Navbar",
  data() {
    return { logo };
  },
};
</script>

<style scoped>
/* Navbar general */
.navbar-custom {
  background-color: #0e0d8a;
  border-bottom-left-radius: 1rem;
  border-bottom-right-radius: 1rem;
}

/* Wrapper: flujo horizontal, width fijo 1440px, height 72px */
.nav-wrapper {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  max-width: 1440px;
  height: 72px;
  padding: 16px 75px;
  margin: 0 auto;
}

/* Logo + texto */
.nav-brand .logo {
  height: 21px;
  width: auto;
}
.brand-text {
  font-size: 1.125rem;
  color: #912626;
  user-select: none;
  margin-left: 0.5rem;
}

/* Links */
.nav-links ul {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
  gap: 2rem;
}
.nav-links a {
  font-family: 'Nunito Sans', sans-serif;
  color: #ffffff;
  text-transform: uppercase;
  font-weight: 500;
  text-decoration: none;
  transition: color 0.2s;
}
.nav-links a:hover {
  color: #00e09b;
}

/* Botón CTA */
.btn-cta {
  font-family: 'Nunito Sans', sans-serif;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 170px;
  height: 40px;
  padding: 8px 16px;
  border-radius: 260px;
  margin-right: 12px;
  white-space: nowrap;

  /* Colores y tipografía */
  background-color: #00DBBC;
  color: #0e0d8a;
  text-transform: uppercase;
  font-weight: 600;

  /* Transiciones */
  transition: background-color 0.2s, transform 0.1s;
}

.btn-cta:hover {
  background-color: #00DBBC;
  transform: translateY(-1px);
}
.btn-cta:active {
  transform: translateY(0);
}
</style>
