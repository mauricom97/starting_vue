<template>
  <div id="app">
    <input type="text" v-model="clienteMauricio.nome"/>

    <div v-for="(cliente, index) in clientes" :key="cliente.id">
      <p>{{index}}</p>
      <cliente :cliente="cliente"/>
      <hr>
      <h4>Edição: </h4>
      <input type="text" v-model="cliente.nome">
      <input type="text" v-model="cliente.email">
    </div>
  </div>
</template>

<script>
import cliente from './components/cliente'
export default {
  name: 'App',
  data(){
          return{
            clienteMauricio: {
              nome: "Mauricio",
              email: "mauricio.nunes@beaudio.com",
              idade: 23
            },
            clientes: [
              {
                id: 0,
                nome: "Mauricio Nunes",
                email: "mauricio.nunes@beaudio.com.br",
                idade: 23
              },
              {
                id: 1,
                nome: "Jhenifer",
                email: "jhenifer_de_melo@hotmail.com",
                idade: 20
              },
              {
                id: 2,
                nome: "Theo",
                email: "theo@gmail.com",
                idade: "10 meses"
              },
                            {
                id: 3,
                nome: "Theo",
                email: "theo@gmail.com",
                idade: "10 meses"
              }
            ]
          }
  },
  components: {
    cliente,
    //produto
  }

}
</script>

<style>

</style>