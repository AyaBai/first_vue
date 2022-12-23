<template>
	<div class="container">
		<div class="library">
			<table class="table" border="1">
				<thead> LIBRARY
					<tr>
						<th>#</th>
						<th>Author</th>
						<th>Book name</th>
						<th>Year</th>
						<th>Genre</th>
						<th>Edit/delete</th>
					</tr>
					
					<tr  v-for="(book, index) in BookList">
						<td>{{ index + 1 }}</td>
						<td>{{book.author}}</td>
						<td>{{book.name}}</td>
						<td>{{book.year}}</td>
						<td>{{getGenre(book.genre)}}</td>
						<td>
							<button class="btn" v-on:click="edit(index, book)">edit</button>
							<!-- слушатель события на кнопке редактировать -->
							<button class="btn" v-on:click="remove(index)">delete</button>
							<!-- удаление -->
						</td>
					</tr>
				</thead>
			</table>
		</div>
	</div>
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
	props: {
		BookList: {
			type: Object,
			required: true
		},
		genres: {
			type: Array,
			required: true
		}
	},
	methods: {
		remove(index) {
			
			this.$emit('delete', index)

		},
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

	* {
		font-family: 'Roboto Mono', monospace;
		font-weight: 500;
	}

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
	
</style>