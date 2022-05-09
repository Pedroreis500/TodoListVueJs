<template>
   <div class="lista-tarefas">
       <template v-if="tarefas.length">
           <tarefas v-for="(tarefa,id) in tarefas" :key="tarefa.nome"
           @removeTarefa="$emit('removeTarefa', id)"
           @marcaComoRealizado="$emit('marcaComoRealizado',id)"
           :tarefa="tarefa">
           </tarefas>
       </template>
       <p v-else class="sem-tarefa">Suas tarefas estão em dia (: </p>
   </div>
</template>

<script>

import tarefas from "./tarefas.vue"

export default {

    components:{tarefas},
    props:{
        tarefas:{type: Array, required: true }
    }
}
</script>


<style>
    .lista-tarefas{
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
    }

    .lista-tarefas .tarefa{
        margin: 10px;
    }

    .sem-tarefa{
        color: #AAA;
        font-size: 1.7em;
    }
</style>