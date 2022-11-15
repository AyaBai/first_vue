<template>
	<div class="container">
		<h1 class="title">To Do List</h1>
		<div class="addlist">
			<input class="input-t" type="text" placeholder="add task" v-model="value" >
			<button class="add-btn" v-on:click="toDoList.push(value)">Add</button>
		</div>
		<div class="list">	
			<ol>
				<li v-for="task in toDoList">
					<label><input class="input-c" type="checkbox" v-model="task.isDone">
					{{task.name}}{{value}}</label>
					<button class="bin"></button>
				</li>				
			</ol>
			<ul>
				<li v-for="task in toDoList">{{task.name}} {{task.isDone}}</li>
			</ul>
		</div>

	</div>
</template>

<script>
	export default {
		data() {
			return {
				value:'',
				toDoList:[
					{
						name:'купить хлеб',
						isDone:true,
					},
					{
						name:'помыть посуду',
						isDone:false,
					}
				],
			}
		},
		methods: {
			update () {

			},
			delete() {

			},
			create () {
				this.toDoList=this.value// взять данные для названия новой задачи, 
				// создать обЪект по образцу элементов toDoList
				// 

			}

		}
	}
</script>

<style>
	.container {
		width: 500px;
		/*outline: 2px solid red;*/
	}

	.title {
		color: #A6979C;
		text-align: center;
	}

	.addlist {
		width: 100%;
		background-color: #D5E2BC;
		border-radius: 10px;
		padding: 15px;
	}

	.add-btn {
		margin: 0 15px;
		height: 30px;
		border-radius: 10px;
		border: none;	
		font-weight: 600;
	}

	.add-btn:hover {
		background-color: #D3C0D2;

	}

	.input-t {
		width: 85%;
		height: 30px;
		font-size: 20px;
		background-color: #D5E2BC;
		padding: 15px;
		border-radius: 10px;
		border: none;
	}


	.input-c {
		color: #A6979C;
	}

	.list {
		background-color: #D3C0D2;
		text-align: left;
		font-size: 20px;
		padding-left: 10px;
		border-radius: 10px;
		margin-top: 15px;
	}

	.bin {
		width: 25px;
		height: 25px;
		background-repeat: no-repeat;
		background-image: url(../img/bin.svg) ;
		background-color: transparent;
		border-color: transparent;
	}

	input:checked {
		background: #DAFFEF;
	}

</style>