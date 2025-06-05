<template>
  <div class="login">
    <h2>Login</h2>
    <form @submit.prevent="login">
      <input v-model="user" placeholder="Usuario" required />
      <input type="password" v-model="pass" placeholder="Contraseña" required />
      <button type="submit">Entrar</button>
    </form>
    <p v-if="error" style="color: red">{{ error }}</p>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const user = ref('')
const pass = ref('')
const error = ref('')

const emit = defineEmits(['login-success'])

function login() {
  // Aquí pones tu validación simple de frontend (usuario y pass)
  if (user.value === 'admin' && pass.value === '1234') {
    emit('login-success')
  } else {
    error.value = 'Usuario o contraseña incorrectos'
  }
}
</script>

<style scoped>
.login {
  max-width: 300px;
  margin: 40px auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
}
.login input {
  width: 100%;
  margin-bottom: 10px;
  padding: 8px;
}
.login button {
  width: 100%;
  padding: 10px;
  background: #007bff;
  color: white;
  border: none;
  cursor: pointer;
}
.login button:hover {
  background: #0056b3;
}
</style>
