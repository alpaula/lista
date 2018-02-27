<template>
	<section class="conteudoAluno">
		<h1 class="titulo">Alunos Vai na Web</h1>
		<ul>
			<li v-for="aluno in lista">
				{{aluno.name}}
				{{aluno.age}} anos
				<hr>
			</li>
		</ul>
	</section>
</template>
<script>
export default{
	name:'ListaAlunos',
	props:{
		lista:{
			type: Array,
			required: true
		}
	},
	data (){

	}
}
</script>
<style scoped>
	.body{
		width: 100%;
	}
	.titulo{
		width: 100%;
		height: 6vh;
		margin: 0;
		padding-top: 2%;
		background: rgb(102,51,153);
		color: #fff;
	}
</style>