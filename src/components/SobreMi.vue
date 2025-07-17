<template>
  <div class="sobre-mi">
    <!-- Logo arriba a la izquierda -->
    <div class="text-start ps-4 pt-4">
      <img src="/logo-iplacex.png" alt="Logo Iplacex" width="300" />
    </div>

    <!-- Contenido principal -->
    <div
      class="container-fluid d-flex flex-column justify-content-center align-items-center"
      style="min-height: calc(100vh - 100px)"
    >
      <div class="row w-100 px-5">
        <!-- Texto a la izquierda -->
        <div class="col-md-6 d-flex flex-column justify-content-center">
          <h2 class="mb-3">Sobre mí</h2>
          <p class="fs-5">
            Soy <strong>Viviana Mardones Henríquez</strong>, estudiante de
            <strong>Analista Programador</strong> en <strong>Iplacex</strong>.
          </p>
          <p class="fs-6">Fecha: julio 2025</p>
          <p>
            Este proyecto es una aplicación web que permite calcular calificaciones y registrar
            usuarios. Utiliza <strong>Vue.js</strong> para la interfaz y
            <strong>Bootstrap</strong> para el diseño responsivo.
          </p>
          <p>Espero que disfruten usando esta aplicación tanto como yo disfruté desarrollándola.</p>
          <p>Profesor: <strong>FELIPE IGOR FLORES VALDEBENITO</strong></p>
        </div>

        <!-- Imagen del teclado a la derecha -->
        <div class="col-md-6 text-center d-flex align-items-center justify-content-center">
          <img
            src="/laptop-hands.jpg.png"
            alt="Laptop"
            class="img-fluid rounded"
            style="max-width: 500px"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.sobre-mi {
  min-height: 100vh;
  width: 100%;
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
}
</style>
