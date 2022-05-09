<template>  
    <div class="novaTarefa">
        <input v-model="nome" @keydown.enter="add" type="text" class="form-element"
        placeholder="Nova tarefa? Ex: Lavar o carro">
        <button @click="add" class="form-element">+</button>
    </div>    
</template>

<script>
export default {
    data() {
        return {
            nome: ''
        }
    },
    methods: {
        add(){
          this.$emit('tarefaAdicionada', {nome: this.nome})
          this.nome = ''
        }
    },
}
</script>


<style>

.novaTarefa{
    margin: 35px;
}

.form-element{
    outline: none;
    font-size: 2rem;
    border: 1px solid #FFF;
    padding: 5px 10px 8px;
    color: #FFF;
}

input.form-element{
    width: 500px;
    background: #FFF2;
    border-top-left-radius: 8px;
    border-bottom-left-radius: 8px;
}

button.form-element{
    border-left: none;
    background-color: #2196f3;
    border-top-right-radius: 8px;
    border-bottom-right-radius: 8px;
}
</style>

