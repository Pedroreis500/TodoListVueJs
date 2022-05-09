<template>
	<div id="app">
		<h1>Tarefas</h1>
		<progressoTarefa :progresso="progresso"></progressoTarefa>
		<novaTarefa @tarefaAdicionada="addTarefa"></novaTarefa>
		<listaTarefas v-bind:tarefas="tarefas" 
		@removeTarefa="DeletaTarefaPeloId"
		@marcaComoRealizado="alternaPendenciaDaTarefa"
		></listaTarefas>

		
	</div>
</template>

<script>
import novaTarefa from './components/novaTarefa.vue'
import progressoTarefa from './components/progressoTarefa.vue'
import listaTarefas from "./components/listaTarefas";
export default 
{
	components: {progressoTarefa, novaTarefa, listaTarefas},
		data()
		{
			return{
				tarefas:[]
			}
		},

		methods: {
			addTarefa(tarefa)
			{
				const tarefaIgual = t =>t.nome === tarefa.nome // compara as tarefas de mesmo nome
				const ehTarefaNova = this.tarefas.filter(tarefaIgual).length == 0 // se o tamanho do filtro de tarefas iguais for 0, a tarefa ainda não existe, é nova
				if(ehTarefaNova)
				{
				this.tarefas.push({nome: tarefa.nome, pendente: tarefa.pendente || true})						
				}
			},

			DeletaTarefaPeloId(id)
			{
				this.tarefas.splice(id,1) // a partir de um id exclui esse elemento do array
			},

			alternaPendenciaDaTarefa(id)
			{
				this.tarefas[id].pendente = !this.tarefas[id].pendente // =  realizado
			}
		},

		computed: {
			progresso()
			{
				const total = this.tarefas.length
				const realizado = this.tarefas.filter(t => !t.pendente).length //filtra e retorna tarefas já realizadas
				return Math.round(realizado/total*100) || 0;
			}
		},
}
</script>

<style>
	body {
		font-family: 'Lato', sans-serif;
		background: linear-gradient(to right, rgb(22, 34, 42), rgb(58, 96, 115));
		color: #FFF;
	}

	#app {
		display: flex;
		flex: 1;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 100vh;
	}

	#app h1 {
		margin-bottom: 5px;
		font-weight: 300;
		font-size: 3rem;
	}
</style>
