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
            :error-message="msgErr"
            @blur="$v.usuario.email.$touch(), mensagemErro()"
            :error="$v.usuario.email.$error"
            />
            <q-input
            v-model="usuario.senha"
            class="q-mb-md"
            color="blue-grey-10"
            type="password"
            label="Senha"
            @blur="$v.usuario.senha.$touch()"
            :error-message="$v.usuario.senha.required ? '' : 'Campo Obrigatorio'"
            :error="$v.usuario.senha.$error"
            />
            <q-btn
            class="q-mt-md full-width"
            color="blue-grey-10"
            label="Entrar"
            @click="entrar()"
            />
          </q-card-section>
        </q-card>
      </div>
    </div>
</template>

<script>
import { required, maxLength, email } from 'vuelidate/lib/validators'
export default {
  name: 'Formulario',
  data () {
    return {
      msgErr: '',
      usuario: {
        email: '',
        senha: ''
      }
    }
  },
  validations: {
    usuario: {
      email: { required, email, maxLength: maxLength(30) },
      senha: { required }
    }
  },
  methods: {
    mensagemErro () {
      this.$v.usuario.email.$touch()
      if (!this.$v.usuario.email.email) {
        this.msgErr = 'Deve ser um E-mail'
      }
      if (!this.$v.usuario.email.required) {
        this.msgErr = 'Campo Obrigatório'
      }
      if (!this.$v.usuario.email.maxLength) {
        this.msgErr = 'Tamanho maximo de 30 caracteres'
      }
    },
    entrar () {
      this.$v.$touch()
      if (!this.$v.$invalid) {
        alert('Tudo certo!!')
      }
    }
  }
}
</script>
