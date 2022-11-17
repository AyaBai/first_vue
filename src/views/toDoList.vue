<template>
	<div class="container">
		<h1 class="title">To Do List</h1>
		<div class="addlist">
			<input class="input-t" type="text" placeholder="add task" v-model="value" >
			<button class="add-btn" v-on:click="create()">Add</button>
		</div>
		<div class="list">	
			<div v-if="!isEditing">
				
				<ol>
					<li v-for="(task, index) in toDoList" :key="index">
						<label><input class="input-c" type="checkbox" v-model="task.isDone">
						{{task.name}}</label>
						<button class="edit" v-on:click="update(index, value)"></button>
						<button class="bin" v-on:click="remove()"></button>
					</li>				
				</ol>
			</div>
			<div v-else>
				<ol>
					<li v-for="(task, index) in toDoList" :key="index">
						<label><input class="input-c" type="checkbox" v-model="task.isDone">
						{{task.name}}</label>
					</li>				
				</ol>

			</div>
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
				selectedIndex:null,
				isEditing:false,
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
			update (index, value) {
				this.value = value
				this.selectedIndex = index
				this.isEditing: true
				this.toDoList.splice(this.selectedIndex,1,this.todo)

			},
			remove (index) {

				this.toDoList.splice(index,1)
				// alert ('hello')

			},
			create () {
				const toDo = {
						name:this.value,
						isDone:false,
					};
					this.toDoList.push(toDo) // взять данные для названия новой задачи, 
				// создать обЪект по образцу элементов toDoList
				// 
				this.value=''

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

	.bin, .edit {
		width: 25px;
		height: 25px;
		background-repeat: no-repeat;
		background-color: transparent;
		border-color: transparent;
	}

	.edit {
		background-image: url(../img/pngegg.png) ;
		outline: 2px solid red;
	}

	.bin {
		background-image: url(../img/bin.svg) ;
	}

	input:checked {
		background: #DAFFEF;
	}

</style>