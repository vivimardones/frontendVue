<script>
// Rename component to NavBar
export default {
  name: 'NavBar',
}
</script>

<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark mb-4">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">Programación Front End</a>

      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarNav"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <a
              class="nav-link"
              :class="{ active: activeTab === 'calificaciones' }"
              href="#"
              @click.prevent="setTab('calificaciones')"
            >
              Cálculo de calificaciones
            </a>
          </li>
          <li class="nav-item">
            <a
              class="nav-link"
              :class="{ active: activeTab === 'registro' }"
              href="#"
              @click.prevent="setTab('registro')"
            >
              Formulario de registro
            </a>
          </li>
          <li class="nav-item">
            <a
              class="nav-link"
              :class="{ active: activeTab === 'construccion' }"
              href="#"
              @click.prevent="setTab('construccion')"
            >
              En construcción
            </a>
          </li>
        </ul>

        <form class="d-flex" @submit.prevent="buscar">
          <input class="form-control me-2" type="search" placeholder="Buscar" v-model="busqueda" />
          <button class="btn btn-outline-light" type="submit">Búsqueda</button>
        </form>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { defineProps, defineEmits, ref } from 'vue'

defineProps({
  activeTab: String,
})

const emit = defineEmits(['update:activeTab'])

const busqueda = ref('')

function setTab(tab) {
  emit('update:activeTab', tab)
}

function buscar() {
  alert(`Buscando: ${busqueda.value}`)
}
</script>
