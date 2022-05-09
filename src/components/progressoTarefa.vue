<template>
    <div class="tarefa-progresso">
        <span class="progresso-valor">{{progresso}}%</span>
        <div class="progresso-barra" :style="{width: progresso + '%'}"></div>
    </div>
</template>

<script>

export default {
    props: 
    {
        progresso: {type: Number, default:0}
    }
}
</script>

<style>
    .tarefa-progresso{
        position: relative;
        width: 80%;
        border: 1px solid #FFF;
        color: #FFF;
        border-radius: 8px;
        margin-bottom: 15px;
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .progresso-barra {
        position: absolute;
        border-radius: 8px;
        height: 100%;
        background-color: #4CAF50;
        align-self: flex-start;
    }

    .progresso-valor {
        z-index: 1;
        font-size: 1.5rem;
    }
</style>

