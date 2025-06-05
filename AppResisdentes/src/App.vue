<template>
  <div id="app">
    <Navbar v-if="isLoggedIn" />
    <LoginViews v-else @login-success="handleLoginSuccess" />
    <router-view v-if="isLoggedIn" />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Navbar from './components/Navbar.vue'
import LoginView from './views/LoginView.vue'


// Estado inicial: no logueado
const isLoggedIn = ref(false)

// Cuando LoginViews emita 'login-success', activamos la sesión
function handleLoginSuccess() {
  isLoggedIn.value = true
  localStorage.setItem('logueado', 'true') // Guardar para persistencia si quieres
}

// Opcional: si quieres que la sesión se mantenga tras refrescar página
if (localStorage.getItem('logueado') === 'true') {
  isLoggedIn.value = true
}
</script>
