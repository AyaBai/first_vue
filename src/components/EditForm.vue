<template>
	<form @submit.prevent>
		<div class="container">	
			<div class="input-book" v-if = "activeBook">
				<!-- v-if Отрисовывает элемент по условию, в зависимости от истинности указанного выражения. При переключении элемент и все содержащиеся в нём директивы / компоненты будут уничтожены и созданы заново. -->
				<p>Edit book</p>
				<input class="main_input" type="text" placeholder="Author" v-model="activeBook.author"/> 
				<!-- v-model Динамически присваиваем значение переменной,
				Создаёт двухстороннюю привязку к элементу ввода формы или к компоненту. -->

				<input class="main_input" type="text" placeholder="Book title" v-model="activeBook.name"/>

				<input class="main_input" type="number" placeholder="Publication year" v-model="activeBook.year"/>

				<div> Genre
					<select  v-model="activeBook.genre">
						<option value="0">Select the genre:</option>

						<!-- деректива v-for создает цикл, указываем отдельный элемент интерации из массива genres  -->
						<template v-for="(genre, index) in genres">
					  	<option :value="genre.id">	{{genre.name}}</option>
					  </template>
					</select>

					
					<button class="btn" v-on:click="update()">Update</button>	
					<!-- v-on:click = "updateList - вешаем слушатель события на кнопку, обновить после изменения (3) -->
				</div>

			</div>
		</div>
	</form>

</template>

<script>
	export default {
		data() {
			return {
				book: {
					author:'',
					name:'',
					year:'',
					selectedIndex: null, 
					genre:0,
					activeBook: null
				}
			}
		},
			// Props передаваемые от родительского компонента дочернему компоненту, типы входных параметров( имя входного параметра: тип (String,Number,Array,Object etc.))
			props: {
				activeBook: Object,
				genres:  Object,
		},

			methods: {
				edit(index, activeBook) {
					this.$emit('edit', index)
					this.activeBook = {
						author:'',
						name:'',
						year:'',
						genre: 0
					}
				},

				// Если событие генерируется в дочернем компоненте в camelCase, то в родительском потребуется прослушивать в kebab-case:
				update(){
					this.$emit('update')
				}
			}
					// for (let book of BookList)
					// {
					// 	if (activeBook = index ) {}


					//  this.activeBook = index;
					// }
				
			}			
		


</script>

<style>
	.container {
/*		min-width: 50%;*/
		font-size: 15px;
		margin-top: 20px;
	}

	.input-book {
		max-width: 300px;
		outline: 2px solid black;
		padding: 15px;
	}

	.main_input {
		width: 100%;
		display: flex;
		margin-bottom: 10px;
	}

</style>