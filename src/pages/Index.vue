<template>
  <q-page class="flex flex-center">
    <div class="row items-center">
      <div class="col-12 items-center">
        <p class="text-h5"> E-mail: {{ email }} </p>
        <p class="text-h5"> Senha: {{ senha }} </p>
        <q-btn color="blue-grey-10" label="Sair" @click="sair()"/>
      </div>
    </div>
  </q-page>
</template>

<script>
export default {
  name: 'Index',
  data () {
    return {
      email: '',
      senha: ''
    }
  },
  mounted () {
    this.recuperarDados()
  },
  methods: {
    recuperarDados () {
      this.email = localStorage.getItem('email')
      this.senha = localStorage.getItem('senha')
    },
    sair () {
      localStorage.clear()
      this.$router.push({ path: '/' })
    }
  }
}
</script>
