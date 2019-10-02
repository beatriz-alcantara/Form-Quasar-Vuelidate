<template>
  <div>
    <div class="row">
      <div class="col-12 items-center">
        <q-card class="my-card">
          <q-card-section style="width: 30vw; height: 35vh;">
            <q-input class="q-mb-md" color="blue-grey-10" type="email" label="E-mail"/>
            <q-input class="q-mb-md" color="blue-grey-10" type="password" label="Senha"/>
            <q-btn class="q-mt-md full-width" color="blue-grey-10" label="Entrar"/>
          </q-card-section>
        </q-card>
      </div>
    </div>
  </div>
</template>

<script>
import { required, maxLength, email } from 'vuelidate/lib/validators'
export default {
  name: 'Formulario',
  data () {
    return {
      usuario: {
        email: '',
        senha: ''
      }
    }
  },
  validations () {
    return {
      usuario: {
        email: { required, email, maxLength: maxLength(30) }
      }
    }
  }
}
</script>
