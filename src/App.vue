<template>
  <div id="app">
   <div class="buttons">
    <button class="button is-primary">Primary</button>
    <button class="button is-link">Link</button>
  </div>
    <h3>Cadastro: </h3>
    <small id="nomeErro" v-show="deuErro">Nenhum dos campos pode ficar em branco!</small><br>
    <input type="text" placeholder="nome" v-model="nomeField"><br>
    <input type="email" placeholder="email" v-model="emailField"><br>
    <input type="number" placeholder="idade" v-model="idadeField"><br><br>
    <button @click="cadastrarUsuario">Cadastrar</button>
    <hr>

    <div v-for="(cliente, index) in orderClientes" :key="cliente.id">
      <p>{{index}}</p>
      <cliente :cliente="cliente" @meDelete="deletarUsuario($event)"/>
    </div>
  </div>
</template>

<script>
import _ from 'lodash';
import cliente from './components/cliente'
export default {
  name: 'App',
  data(){
          return{
            deuErro: false,
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
      if(this.nomeField == '' || this.emailField == '' || this.idadeField == ''){
        this.deuErro = true
      }else{
      this.clientes.push({nome: this.nomeField, email: this.emailField, idade: this.idadeField, id: Date.now()})
      this.nomeField = ''
      this.emailField = ''
      this.idadeField = ''

      this.deuErro = false
     }
    },
    deletarUsuario: function($event){
      var id = $event.idCliente;
      var novoArray = this.clientes.filter(cliente => cliente.id != id);
      this.clientes = novoArray
    }
  },
  computed: {
    orderClientes: function(){
      return _.orderBy(this.clientes,['nome'],['asc']);
    }
  }
}
</script>

<style>
#nomeErro{
  color: red;
}
</style>