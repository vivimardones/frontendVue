<template>
  <form @submit.prevent="calcular">
    <div class="mb-3 w-50 mx-auto">
      <label for="nota1" class="form-label text-center d-block">Nota 1</label>
      <input
        type="number"
        class="form-control"
        id="nota1"
        v-model.number="nota1"
        min="10"
        max="70"
        placeholder="Nota 1"
        required
      />
    </div>

    <!-- Nota 2 -->
    <div class="mb-3 w-50 mx-auto">
      <label for="nota2" class="form-label text-center d-block">Nota 2</label>
      <input
        type="number"
        class="form-control"
        id="nota2"
        v-model.number="nota2"
        min="10"
        max="70"
        placeholder="Nota 2"
        required
      />
    </div>

    <!-- Nota 3 -->
    <div class="mb-3 w-50 mx-auto">
      <label for="nota3" class="form-label text-center d-block">Nota 3</label>
      <input
        type="number"
        class="form-control"
        id="nota3"
        v-model.number="nota3"
        min="10"
        max="70"
        placeholder="Nota 3"
      />
    </div>

    <!-- Asistencia -->
    <div class="mb-3 w-50 mx-auto">
      <label for="asistencia" class="form-label text-center d-block">Asistencia (%)</label>
      <input
        type="number"
        class="form-control"
        id="asistencia"
        v-model.number="asistencia"
        min="0"
        max="100"
        placeholder="Asistencia"
        required
      />
    </div>

    <!-- Botón calcular -->
    <div class="text-center mb-3">
      <button type="submit" class="btn btn-primary">Calcular</button>
    </div>
    <div class="text-center mb-3 text-danger">
      <p>{{ error }}</p>
    </div>
    <!-- Resultado -->
    <div v-if="resultado" class="alert text-center d-block" :class="resultadoClase">
      <p>{{ resultado }}</p>
      <p>{{ estado }}</p>
    </div>
  </form>
</template>

<script setup>
import { ref } from 'vue'

const nota1 = ref(null)
const nota2 = ref(null)
const nota3 = ref(null)
const asistencia = ref(null)
const estado = ref('')

const error = ref('')

const resultado = ref('')
const resultadoClase = ref('')

function validar() {
  if (
    nota1.value < 10 ||
    nota1.value > 70 ||
    nota2.value < 10 ||
    nota2.value > 70 ||
    nota3.value < 10 ||
    nota3.value > 70 ||
    asistencia.value < 0 ||
    asistencia.value > 100
  ) {
    error.value = 'Por favor, ingresa valores válidos para las notas y asistencia.'
    return false
  }
  error.value = ''
  return true
}

function calcular() {
  resultado.value = ''
  resultadoClase.value = ''

  if (!validar()) return

  const promedio = nota1.value * 0.35 + nota2.value * 0.35 + nota3.value * 0.3

  if (promedio >= 40 && asistencia.value >= 80) {
    resultado.value = `El Promedio es: ${promedio.toFixed(2)}`
    estado.value = 'Tu estado es: Aprobado'
    resultadoClase.value = 'alert-success'
  } else {
    resultado.value = `El Promedio es: ${promedio.toFixed(2)}`
    estado.value = 'Tu estado es: Reprobado'
    resultadoClase.value = 'alert-danger'
  }
}
</script>
