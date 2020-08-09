<template>
  <div id="app">
    <h3>Cadastro: </h3>
    <input type="text" placeholder="nome" v-model="nomeField"><br>
    <input type="text" placeholder="email" v-model="emailField"><br>
    <input type="number" placeholder="idade" v-model="idadeField">
    <button @click="cadastrarUsuario">Cadastrar</button>
    <hr>

    <div v-for="(cliente, index) in clientes" :key="cliente.id">
      <p>{{index}}</p>
      <cliente :cliente="cliente"/>
    </div>
  </div>
</template>

<script>
import cliente from './components/cliente'
export default {
  name: 'App',
  data(){
          return{
            nomeField: "",
            emailField: "",
            idadeField: 0,
          clientes: [
              {
                id: 0,
                nome: "Mauricio Nunes",
                email: "mauricio.nunes@beaudio.com.br",
                idade: 23
              },

            ]
          }
  },
  components: {
    cliente,
    //produto
  },
  methods: {
    cadastrarUsuario: function(){
      this.clientes.push({nome: this.nomeField, email: this.emailField, idade: this.idadeField, id: Date.now()})
      this.nomeField = ''
      this.emailField = ''
      this.idadeField = ''
    }
  }

}
</script>

<style>

</style>