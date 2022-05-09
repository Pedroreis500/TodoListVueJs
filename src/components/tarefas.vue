<template>
    <div 
    @click="$emit('marcaComoRealizado', tarefa)"
    class="tarefa" v-bind:class="estadoTarefa">
    <span @click.stop="$emit('removeTarefa', tarefa)" class="excluir">X</span>
    <p>{{tarefa.nome}}</p>
    </div>
</template>

<script>
export default {
    props:{ 
        tarefa:{type:Object, required:true}
    },
        computed: 
        {
            estadoTarefa()
            {
                return{
                  pendente: this.tarefa.pendente, // aplica uma classe css pendente a tarefa pendente
                  realizado:!this.tarefa.pendente
                }
            }
        
        },
}
</script>

<style>
    .tarefa{
        position: relative;
       box-sizing: border-box; 
       width: 350px;
       height: 140px;
       padding: 10px;
       border-radius: 8px;
       font-size: 2em;
       font-weight: 300;
       cursor: pointer;
       /*user-select: none;*/
       justify-content: center;
       align-items: center;
    }
    .pendente{
        border-left: 12px solid #B73229;
        background-color: #F44336;
    }
    .realizado{
        color: #DDD;
        border-left: 12px solid #0A8F08;
        background-color:#4CAF50 ;
        text-decoration: line-through;
    }
    .pendente .excluir{
        background-color: #B73229;
    }
    .realizado .excluir{
        background-color: #0A8F08;
     }
    .excluir{
        position: absolute;
        right: 10px;
        top: 10px;
        font-size: 0.9rem;
        font-weight: 600;
        height: 20px;
        width: 20px;
        border-radius: 20px;
        display: flex;
        justify-content: center;
    }
</style>
