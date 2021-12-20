<script>
	import Menubar from './views/Menubar.svelte';
	// import MovieSummary from './views/MovieSummary.svelte';
	// import {openModal} from "./utils/Modal.svelte";
	// import Actor from './views/Actor.svelte';
	// import Movie from './views/Movie.svelte';
	// import { onMount } from "svelte";
	// import GetParams from './views/GetParams.svelte';
	// import AddMovie from "./views/AddMovie.svelte";
	
	// let search;
	// let errorMsg;
	// let movies = [];
	// let allMovies = [];
	// let selectedMovie;
	// let selectedActor;
	// let selectedMovies = [];

	// let getParams = {
	// 	limit: 12,
	// 	offset: 0,
	// 	orderBy: 'none',
	// 	orderDir: 'asc'
	// }

	// async function fillMovies() {
	// 	getParams.offset = getParams.offset >=0 ? getParams.offset : 0;
	// 	let order = getParams.orderBy == 'none' ? "" : "&order-by=" + getParams.orderBy + "&order-dir=" + getParams.orderDir;
	// 	// offset does not work on :3002
	// 	await fetch("http://localhost:3001" + '/movies?limit=' + getParams.limit + '&offset=' + getParams.offset + order)
	// 	.then(async (response) => {
	// 		movies = await response.json();
	// 		allMovies = movies;
	// 	})
	// }

	// onMount(async () => {fillMovies().then(() => open(movies[0].id)) });

	// async function open(id) {
	// 	let search = selectedMovies.filter((item) => item.id== id);
	// 	if ( search.length > 0) {
	// 		selectedMovie = search[0].movie;
	// 	} else {
	// 		await fetch("http://localhost:3002" + "/movies/" + id)
	// 		.then(async (response) => {
	// 			selectedMovie = await response.json();
	// 			selectedMovies.push({id:id,movie: selectedMovie});
	// 		})
	// 		.catch(error => errorMsg = error); 
	// 	}
	// }

	// const filterMovies = () => {
	// 	if (!search) {
	// 		movies = allMovies;
	// 	} else {
	// 		movies = allMovies.filter((movie) => movie.title.toLowerCase().includes(search.toLowerCase()));
	// 		if (movies[0]) { open(movies[0].id);}
	// 	}
	// }

</script>

<Menubar/>

<!-- <Actor actor={selectedActor} on:openMovie={(event) => open(event.detail)}/>

<GetParams on:useGetParams={fillMovies} on:updateGetParams={(event) => getParams = event.detail}/>

<AddMovie on:addedMovie={fillMovies}/>	 -->

<main class="container">
	
	<!-- {#if errorMsg}
		<div class="alert alert-danger">{errorMsg}</div>
	{/if} -->

	<div class="row">
		<div class="col-md-4">
			<!-- {#if selectedMovie}
				<Movie movie={selectedMovie} on:openActor={(event) => selectedActor = event.detail} on:deletedMovie={() => fillMovies().then(open(movies[1].id)) }/>
			{/if} -->
		</div>
		<div class="col-md">
			<!-- <input type="text" class="form-control" bind:value={search} on:input={filterMovies}> -->
			
			<!-- <div class="form row">
				<button class="btn btn-primary col m-1" on:click={async () => {getParams.offset -= getParams.limit; fillMovies()}}>Back</button>
				<button class="btn btn-outline-secondary col m-1" on:click={() => {getParams.offset = 0; getParams.limit = 12; getParams.orderBy = 'none'; getParams.orderDir='asc'; fillMovies()}}>Reset</button>
				<h6 class="col text-center m-3">Page: {(getParams.offset/getParams.limit).toFixed(0)}</h6>
				<button class="btn btn-outline-secondary col m-1" on:click={() => openModal("settings")}>Settings</button>
				<button class="btn btn-primary col m-1" on:click={async () => {getParams.offset += getParams.limit; fillMovies()}}>Next</button>
			</div> -->

			<div class="row row-cols-2 g-2">
				<!-- {#each movies as movie}
					<MovieSummary {movie} on:click={async () => { await open(movie.id) }}/>
				{/each} -->
			</div>
		</div>
	</div>
</main>