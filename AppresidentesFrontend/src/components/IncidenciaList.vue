<template>
  <div class="container mt-4">
    <h2 class="mb-4">Lista de Incidencias</h2>
    <ul class="list-group">
      <li
        v-for="incidencia in incidencias"
        :key="incidencia.id"
        class="list-group-item d-flex justify-content-between align-items-center"
      >
        <div>
          <strong>{{ incidencia.descripcion }}</strong><br />
          <small>{{ incidencia.fecha }} {{ incidencia.hora }}</small><br />
          <span class="badge bg-info text-dark">Estado: {{ incidencia.estado }}</span>
        </div>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'

const incidencias = ref([])

const cargarIncidencias = async () => {
  try {
    const response = await axios.get('/incidencias')
    incidencias.value = response.data
  } catch (error) {
    console.error('Error al cargar las incidencias:', error)
  }
}

onMounted(() => {
  cargarIncidencias()
})
</script>
