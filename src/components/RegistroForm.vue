<template>
  <form @submit.prevent="submitForm">
    <!-- Nombre -->
    <div class="mb-3 w-50 mx-auto text-center">
      <label for="name" class="form-label">Nombre</label>
      <input
        type="text"
        class="form-control"
        id="name"
        v-model="form.name"
        @input="validateName"
        required
        placeholder="Tu nombre"
      />
      <p v-if="errors.name" class="text-danger">{{ errors.name }}</p>
    </div>

    <!-- Correo -->
    <div class="mb-3 w-50 mx-auto text-center">
      <label for="correo" class="form-label">Correo</label>
      <input
        type="email"
        class="form-control"
        id="email"
        v-model="form.email"
        @input="validateEmail"
        required
        placeholder="ejemplo@correo.com"
      />
      <p v-if="errors.email" class="text-danger">{{ errors.email }}</p>
    </div>

    <!-- Contraseña -->
    <div class="mb-3 w-50 mx-auto text-center">
      <label for="password" class="form-label">Contraseña</label>
      <input
        type="password"
        class="form-control"
        id="password"
        v-model="form.password"
        @input="validatePassword"
        required
        placeholder="Contraseña"
      />
      <p v-if="errors.password" class="text-danger">{{ errors.password }}</p>
    </div>

    <!-- Confirmar contraseña -->
    <div class="mb-3 w-50 mx-auto text-center">
      <label for="confirmar" class="form-label">Repitir contraseña</label>
      <input
        type="password"
        class="form-control"
        id="password2"
        v-model="form.password2"
        @input="validatePassword2"
        required
        placeholder="Repite la contraseña"
      />
      <p v-if="errors.password2" class="text-danger">{{ errors.password2 }}</p>
    </div>

    <!-- Botón enviar -->
    <div class="text-center mb-3">
      <button type="submit" class="btn btn-success">Enviar</button>
    </div>

    <!-- Mensaje de error -->
    <div v-if="error" class="alert alert-warning text-center w-50 mx-auto">
      {{ error }}
    </div>

    <!-- Mensaje de éxito -->
    <div v-if="exito" class="alert alert-success text-center w-50 mx-auto">
      {{ exito }}
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      form: {
        name: '',
        password: '',
        password2: '',
        email: '',
      },
      errors: {
        name: '',
        password: '',
        password2: '',
        email: '',
      },
    }
  },
  methods: {
    validateName() {
      if (!this.form.name) {
        this.errors.name = 'El campo nombre es requerido'
      } else if (/\d/.test(this.form.name)) {
        this.errors.name = 'El nombre no debe contener números'
      } else {
        this.errors.name = ''
      }
    },
    validatePassword() {
      if (!this.form.password) {
        this.errors.password = 'El campo contraseña es requerido'
      } else if (this.form.password.length < 5) {
        this.errors.password = 'La contraseña debe tener al menos 5 caracteres'
      } else {
        this.errors.password = ''
      }
    },
    validatePassword2() {
      if (!this.form.password2) {
        this.errors.password2 = 'El campo repetir contraseña es requerido'
      } else if (this.form.password2 != this.form.password) {
        this.errors.password2 = 'Las contraseñas no coinciden'
      } else {
        this.errors.password2 = ''
      }
    },
    validateEmail() {
      if (!this.form.email) {
        this.errors.email = 'El campo correo es requerido'
      } else if (!/^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/.test(this.form.email)) {
        this.errors.email = 'El correo es inválido'
      } else {
        this.errors.email = ''
      }
    },
    submitForm() {
      this.validateName()
      this.validatePassword()
      this.validatePassword2()
      this.validateEmail()

      if (!Object.values(this.errors).some((error) => error !== '')) {
        alert('El registro se ha realizado correctamente')
      }
    },
  },
}
</script>
