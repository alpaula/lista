<template>
	<div class="body">
		<section class="conteudoAluno">
			<h1 class="titulo">Classificar</h1><br>
			<form>
				<div>
					<label>Ordenar por:</label>
					<select v-model="configs.orderBy">
						<option value="name">Nome</option>
						<option value="age">Idade</option>
					</select>
				</div><br>
				<div>
					<label>Ordem:</label>
					<select v-model="configs.order">
						<option value="asc">Crescente</option>
						<option value="desc">Decrescente</option>
					</select>
				</div><br>
				<div>
					<label>Filtrar:</label>
					<input type="text" placeholder="Filtrar por nome" v-model="configs.filter">
				</div>
			</form>
		</section>
		<ListaAlunos v-bind:lista="lista"></ListaAlunos>
	</div>
</template>
<script>
import _ from 'lodash'
import ListaAlunos from './ListaAlunos.vue'
export default{
	name: 'Lista',
	data (){
		return{
			configs:{
				orderBy:'name',
				order:'asc',
				filter:''
			},
			alunos:[
				{
					name: 'Anna Luiza',
					age: '25'
				},
				{
					name: 'Gabriel Milão',
					age: '22'
				},
				{
					name: 'Caio Gusmão',
					age: '17'
				},
				{
					name: 'Geraldo',
					age: '22'
				},
				{
					name: 'Rafael',
					age: '17'
				},
				{
					name: 'Guilherme Maria',
					age: '17'
				},
			]
		}
	},
	computed:{
		lista(){
			const filter = this.configs.filter;
			const lista = _.orderBy(this.alunos, this.configs.orderBy, this.configs.order);

			if (_.isEmpty(filter)) {
				return lista;
			}

			return _.filter(lista, aluno => aluno.name.indexOf(filter) >= 0);
		},
	},
	components:{
		ListaAlunos
	}
}
</script>
<style scoped>
	.body{
		width: 100%;
		min-height: 44vh;
		padding: 0;
		margin: 0;
		background: rgba(102,51,153,0.3);
		display: flex;
		justify-content: flex-start;
		align-items: flex-start;
	}
	.conteudoAluno{
		width: 50%;
	}
	.titulo{
		width: 100%;
		height: 6vh;
		margin: 0;
		padding-top: 2%;
		background: rgb(102,51,153);
		color: #fff;
	}
	select{
		border-radius: 4px;
	}
	input{
		border-radius: 4px;
		text-align: center;
	}
	li{
		list-style-type: none;
	}
</style>