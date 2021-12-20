<script>
    import Card from "../utils/Card.svelte";
    // import ActorSummary from "./ActorSummary.svelte";
    // import { createEventDispatcher } from 'svelte';
    // const dispatch = createEventDispatcher();

    // export let movie = {
    //     "id": 0,
    //     "title": "string",
    //     "description": "string",
    //     "year": 0,
    //     "rating": "string",
    //     "review": {
    //         "user": 10,
    //         "userCount": 0,
    //         "metaScore": 100
    //     },
    //     "languages": [
    //         "string"
    //     ],
    //     "actors": [
    //         {
    //         "id": 0,
    //         "name": "string"
    //         }
    //     ],
    //     "imdb_url": "string"
    // }

    // let ourReview = 7;

    // function addAvg(x,avg,n) {
    //     return ((avg*(n-1) + x)/n).toString(); 
    // }

    // async function sendReview() {
    //     movie.review.userCount++;
    //     movie.review.user = addAvg(ourReview,movie.review.user,movie.review.userCount);
    //     fetch("http://localhost:3002" +"/movies/" + movie.id, {
    //         method: 'PUT',
    //         headers:{
    //         'Content-Type':'application/json'
    //         },
    //         body: JSON.stringify(movie)
    //     }).then( (response) => {
    //         if (!response.ok) {
    //             alert(response.status + ": " + response.statusText);
    //         }
    //     });
    // }

    // async function deleteMovie() {
    //     if (!confirm("Are you sure to delete " + movie.title + "?")) return;
    //     fetch("http://localhost:3002/movies/" + movie.id, {
    //         method: "DELETE",
    //         headers:{
    //         'Content-Type':'application/json'
    //         }
    //     }).then((response) => {
    //         if (!response.ok) {
    //             alert(response.status + ": " + response.statusText);
    //         } else {
    //             dispatch("deletedMovie");
    //         }
    //     });
    // }

</script>

<Card title={movie.title}>
    <!-- <a href={movie.imdb_url} alt="{movie.name} imdb link">See on imdb</a>
    <p>Rating: {movie.rating} </p>
    <p>Year: {movie.year}</p>
    <p>Languages: 
        {#each movie.languages as lang,i}
            {i == movie.languages.length - 1  ? lang : lang  + ', ' }
        {/each}
    </p>
    <Card title={"Reviews"}>
        Meta score: {movie.review.metaScore}/100 <br>
        <!-- userscore has trailing zero's -->
        <!-- User score: {movie.review.user.slice(0,3)} <br>
        User count: {movie.review.userCount}
        <form class="form" on:submit|preventDefault={sendReview}>
            <label for="customRange3" class="form-label">Our review: {ourReview} </label>
            <input type="range" class="form-range" min="0" max="10" step="0.5" id="customRange3" bind:value={ourReview}>
            <div class="row m-2">
                <button class="btn btn-primary btn-block">Send our review</button>
            </div>
        </form>
    </Card>
    <div>
        <h5>Actors</h5>
        {#each movie.actors as actor}
            <div class="col-sm">
                <ActorSummary {actor} on:openActor/>
            </div>
        {/each}
    </div>
    <div class="row m-2"> 
        <button on:click={deleteMovie} class="btn btn-outline-danger">Delete</button>
    </div> -->
</Card>

<style>
    /* p {
        margin-bottom: 0;
    } */
</style>