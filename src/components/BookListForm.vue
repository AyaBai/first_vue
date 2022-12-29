<template>
	<form @submit.prevent>
		<div class="container">
			
			<h1>BOOK STORE</h1>
			<div class="input-book">
				<!-- <input class="main_input" type="number" placeholder="# List number" v-model="number"/> -->

				<input class="main_input" type="text" placeholder="Author" v-model="book.author"/> 
				<!-- v-model - двухсторонняя привязка -->

				<input class="main_input" type="text" placeholder="Book title" v-model="book.name"/>

				<input class="main_input" type="number" placeholder="Publication year" v-model="book.year"/>

				<div> Genre
					<select  v-model="book.genre">
						<option value="0">Select the genre:</option>

						<!-- деректива v-for создает цикл, указываем отдельный элемент интерации из массива genres  -->
						<template v-for="(genre, index) in genres">
					  	<option :value="genre.id">	{{genre.name}}</option>
					  </template>
					</select>

					<button class="btn" v-on:click="create(book)" @keyup.enter="onPressEnter">Add book</button>
					<!-- v-on:click - вешаем слушатель события на кнопку, создать (1)-->
					<!-- <button class="btn" v-on:click="updateList()">Update</button>	 -->
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
				genre:0
			}
		}
	},

	methods:{
		create (book) {
				// создает "полку с книгой"
				// const books = {
				// 	author:this.author,
				// 	name:this.name,
				// 	year:this.year,
				// 	genre:this.genre,

				// };
			this.book.id = Date.now();
			this.$emit('create', this.book)
			this.book = {
				author:'',
				name:'',
				year:'',
				genre: 0
			}

				// this.BookList.push(books)
				// console.log(this.book)
			}			
	},

	props: {
		genres: {
			type: Array,
			required: true
		}
	}	

}
	
</script>

<style scoped>
	* {
		font-family: 'Roboto Mono', monospace;
		font-weight: 500;
	}

	.container {
		min-width: 50%;
		font-size: 15px;
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

	.btn {
		margin-right: 10px;
		background: none;
	}
	
=======
<template>
	<form @submit.prevent>
		<div class="container">
			
			<h1>BOOK STORE</h1>
			<div class="input-book">
				<!-- <input class="main_input" type="number" placeholder="# List number" v-model="number"/> -->

				<input class="main_input" type="text" placeholder="Author" v-model="book.author"/> 
				<!-- v-model - двухсторонняя привязка -->

				<input class="main_input" type="text" placeholder="Book title" v-model="book.name"/>

				<input class="main_input" type="number" placeholder="Publication year" v-model="book.year"/>

				<div> Genre
					<select  v-model="book.genre">
						<option value="0">Select the genre:</option>

						<!-- деректива v-for создает цикл, указываем отдельный элемент интерации из массива genres  -->
						<template v-for="(genre, index) in genres">
					  	<option :value="genre.id">	{{genre.name}}</option>
					  </template>
					</select>

					<button class="btn" v-on:click="create(book)" @keyup.enter="onPressEnter">Add book</button>
					<!-- v-on:click - вешаем слушатель события на кнопку, создать (1)-->
					<button class="btn" v-on:click="updateList()">Update</button>	
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
				genre:0
			}
		}
	},

	methods:{
		create (book) {
				// создает "полку с книгой"
				// const books = {
				// 	author:this.author,
				// 	name:this.name,
				// 	year:this.year,
				// 	genre:this.genre,

				// };
			this.book.id = Date.now();
			this.$emit('create', this.book)
			this.book = {
				author:'',
				name:'',
				year:'',
				genre: 0
			}

				// this.BookList.push(books)
				// console.log(this.book)
			}	
			
	},

	props: {
		genres: {
			type: Array,
			required: true
		}
	}	

}
	
</script>

<style scoped>
	* {
		font-family: 'Roboto Mono', monospace;
		font-weight: 500;
	}

	.container {
		min-width: 1024px;
		font-size: 15px;
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

	.btn {
		margin-right: 10px;
		background: none;
	}
	
>>>>>>> 04963273793b81d49288b6ed39a8aea626b6f5ea
</style>
