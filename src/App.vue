<template>
  <div id="app">
    <input type="text" v-model="clienteMauricio.nome"/>
      <cliente :cliente="clienteMauricio" :showIdade="true"/>
      <cliente :cliente="clienteMauricio" :showIdade="true"/>
      <cliente :cliente="clienteMauricio" :showIdade="false"/>
      <cliente :cliente="clienteMauricio" :showIdade="false"/>
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
            }
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