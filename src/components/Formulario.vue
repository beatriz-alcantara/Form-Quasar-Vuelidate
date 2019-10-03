<template>
    <div class="row full-width justify-center">
      <div
      class="col-6 items-center">
        <q-card
        class="my-card">
          <q-card-section class="collumn col-12 full-width">
            <q-input
            v-model="usuario.email"
            class="q-mb-md"
            color="blue-grey-10"
            type="email"
            label="E-mail"
            :error-message="mensagemErro('email')"
            :error="$v.usuario.email.$invalid"
            counter
            maxlength="30"
            />
            <q-input
            v-model="usuario.senha"
            class="q-mb-md"
            color="blue-grey-10"
            type="password"
            label="Senha"
            :error-message="mensagemErro('senha')"
            :error="$v.usuario.senha.$invalid"
            counter
            maxlength="10"
            @keyup.enter="entrar()"
            />
            <q-btn
            class="q-mt-md full-width"
            :color="$v.usuario.$invalid ? 'grey' : 'blue-grey-10'"
            label="Entrar"
            @click="entrar()"
            :disable="$v.usuario.$invalid"
            />
          </q-card-section>
        </q-card>
      </div>
    </div>
</template>

<script>
import { required, maxLength, email, minLength } from 'vuelidate/lib/validators'
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
  validations: {
    usuario: {
      email: { required, email, maxLength: maxLength(30) },
      senha: { required, minLength: minLength(4), maxLength: maxLength(10) }
    }
  },
  methods: {
    mensagemErro (campo) {
      if (campo === 'email') {
        if (!this.$v.usuario.email.email) return 'Deve ser um E-mail'
        if (!this.$v.usuario.email.required) return 'Campo Obrigatório'
        if (!this.$v.usuario.email.maxLength) return 'Tamanho maximo de 30 caracteres'
      }
      if (campo === 'senha') {
        if (!this.$v.usuario.senha.minLength) return 'Tamanho mínimo de 4 caracteres'
        if (!this.$v.usuario.senha.required) return 'Campo Obrigatório'
        if (!this.$v.usuario.senha.maxLength) return 'Tamanho máximo de 10 caracteres'
      }
    },
    entrar () {
      this.$v.$touch()
      if (!this.$v.$invalid) {
        localStorage.setItem('email', this.usuario.email)
        localStorage.setItem('senha', this.usuario.senha)
        this.$router.push({ path: '/index' })
      }
    },
    mostrar () {
      console.log(this.idade)
    }
  }
}
</script>
