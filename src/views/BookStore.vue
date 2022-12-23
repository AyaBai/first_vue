
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Roboto+Mono:wght@100;300;500&display=swap" rel="stylesheet">

<template> 
	<!-- подписаться на событие -->
	<BookListForm 
		v-bind:genres="genres"
		@create="create" 

		></BookListForm>

	
	<BookListTable
		 v-bind:BookList="BookList"
		 v-bind:genres="genres"
		 @delete="remove"

		 ></BookListTable>	
</template>

<script>
	import BookListForm from '../components/BookListForm.vue'
	import BookListTable from '../components/BookListTable.vue'

	export default {
		components:{
			BookListForm, BookListTable
		},

		data() {
			// объекты, интерполяция, встраивается в шаблон {{}}
			return {
				author:'',
				name:'',
				year:'',
				selectedIndex: null, 
				genre:0,

				genres:[
					{
						id: 1,
						name: 'Thriller & Spy Fiction',
					},
					{
						id: 2,
						name: 'Sci-fi',
					},
					{
						id: 3,
						name: 'Romance',
					},
						{
						id: 4,
						name: 'Kids',
					},
					{
						id: 5,
						name: 'Lifestyle & Sport',
					},
				],

				BookList:[
					{
						number: 1,
						author: 'Ian Fleming',
						name:'Dr.No',
						year:1958,
						genre: 1
					},				
				],
			}
		},

		methods: {
			// функции
			create (book) {
				// console.log("hello", book)
				// создает "полку с книгой"
				// const books = {
				// 	author:this.author,
				// 	name:this.name,
				// 	year:this.year,
				// 	genre:this.genre,

				// };
				this.BookList.push(book)
				
				// this.author='';
				// this.name='';
				// this.year='';
				// this.genre= 0;
			},	

			// по аргументу index удаляет(splice) из массива данных выбранный элемент
			remove (index) {
				this.BookList.splice(index, 1)
			},

			// по аргументу index,book переназначаем параметры переменных (ребенок-родитель)

			edit (index, book) {
				this.author= book.author;
				this.name= book.name;
				this.year= book.year;
				this.genre= book.genre;
				this.selectedIndex = index
				// console.log(index)

			},

			// создаем переменную по шаблону в data, удаляем выделенный элемент массива, заменяя его новой переменной по структуре основного шаблона, обнуляем поля переменных

			updateList () {
				const bookEdit = {
					author:this.author,
					name:this.name,
					year:this.year,
					genre:this.genre,

				};
				this.BookList.splice(this.selectedIndex, 1, bookEdit)
				this.author='';
				this.name='';
				this.year='';
				this.genre= 0;

			},

			//  список элементов жанров, для отрисовки в выпада
			getGenre (genreId) {
				for (let genre of this.genres) //переменная genre 
				{
					if (genreId == genre.id)
						{return genre.name}
										
				}
				// на входе id, на выходе name жанра из списка жанров.
			},
		}
	}

</script>


<style scoped>
	.container {
		min-width: 1024px;
		font-size: 15px;
	}

	.btn {
		margin-right: 10px;
		background: none;
	}

	.library {
		width: 100%;
		margin-top: 10px;
		outline: 2px solid black;
		padding: 15px;
	}

	.table {
		width: 100%;
		border: 1px solid dimgrey;
		text-align: center;
	}
	

	* {
		font-family: 'Roboto Mono', monospace;
		font-weight: 500;
	}	

</style>