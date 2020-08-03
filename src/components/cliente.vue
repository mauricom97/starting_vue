<template>
    <div :class="{'cliente': !isPremium, 'cliente-premium': isPremium}">
        <p>Nome:  {{cliente.nome}}</p>
        <p>Email: {{cliente.email}}</p>
        <p v-if="2 == 3">Idade: {{cliente.idade}}</p>
        <p v-else>Não informado</p>
        

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

</style>