<template>
    <div :class="{'cliente': !isPremium, 'cliente-premium': isPremium}">
        <p>Nome:  {{cliente.nome}}</p>
        <p>Email: {{cliente.email | processarEmail}}</p>
        <p v-if="2 == 3">Idade: {{cliente.idade}}</p>
        <p v-else>Não informado</p>
        <button @click="mudarCor($event)">Mudar cor</button>
        <button @click="emitirEventoDelete">Deletar</button>

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
    }
    
}
</script>


<style  scoped>
    .cliente{
        background-color: cadetblue;
        max-width: 520px;
        height: 250px;
        padding: 2%;
        margin-top: 2%;
        
    }

    .cliente-premium{
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