<template>
    <div :class="{'cliente': !isPremium, 'cliente-premium': isPremium}">
        <p>Nome:  {{cliente.nome}}</p>
        <p>Email: {{cliente.email | processarEmail}}</p>
        <p v-if="cliente.idade != '' ">Idade: {{cliente.idade}}</p>
        <p v-else>Não informado</p>
        <button @click="mudarCor($event)">Mudar cor</button>
        <button @click="emitirEventoDelete">Deletar</button>
        <h4>Id especial: {{idEspecial}}</h4>


    </div>
</template>


<script>
export default {
    data(){
        return{
            isPremium: false
        }
    },
    props:{
        cliente: Object,
        showIdade: Boolean
    },
    methods:{
        mudarCor: function($event){
            console.log($event)
            this.isPremium = !this.isPremium
        },
        emitirEventoDelete: function(){
            console.log("Emitindo do filho!")
            this.$emit("meDelete", {idCliente: this.cliente.id, curso: "Vue", emProducao: true, component: this})
        },
        testar: function(){
            console.log('Testando para valer')
            alert("Isso é um alert")
        }
    },
    filters: {
        processarEmail: function(value){
            return value.toUpperCase();
        }
    },
    computed: {
        idEspecial: function(){
            return(this.cliente.email + this.cliente.nome + this.cliente.id).toUpperCase();
        }
    }
    
}
</script>


<style  scoped>
    .cliente{
        border-radius: 20px;
        background-color: cadetblue;
        max-width: 520px;
        height: 250px;
        padding: 2%;
        margin-top: 2%;
        
    }

    .cliente-premium{
        border-radius: 20px;
        background-color: black;
        color: yellow;
        max-width: 520px;
        height: 250px;
        padding: 2%;
        margin-top: 2%;
        
    }
    button{
        background-color: turquoise;
    }

</style>