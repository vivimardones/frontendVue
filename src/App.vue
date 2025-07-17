<script setup>
import { ref } from 'vue'
import Navbar from './components/Navbar.vue'
import CalificacionesForm from './components/CalificacionesForm.vue'
import RegistroForm from './components/RegistroForm.vue'
import EnConstruccion from './components/EnConstruccion.vue'
import SobreMi from './components/SobreMi.vue'

const activeTab = ref('calificaciones')
</script>

<template>
  <Navbar :activeTab="activeTab" @update:activeTab="activeTab = $event" />

  <div class="container">
    <CalificacionesForm v-if="activeTab === 'calificaciones'" />
    <RegistroForm v-else-if="activeTab === 'registro'" />
    <SobreMi v-else-if="activeTab === 'sobreMi'" />
    <EnConstruccion v-else />
  </div>
</template>
