<script>
    import Modal from '../utils/Modal.svelte';
    import MultipleInput from '../utils/MultipleInput.svelte';
    import {closeModal} from "../utils/Modal.svelte";
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();

    let newMovie = {
        title: "test movie",
        description: "...",
        year: 1842,
        rating: "ZZZ",
        review: {
            user: 7,
            userCount: 10,
            metaScore: 88,
        },
        actors: [],
        languages: ["English","French"],
        
        imdb_url: "https://imdb.com/"
    }

    let actors = ["Chris Evans"];

    let getLanguages;
    let getActors;

    async function addMovie() {
        getLanguages();
        getActors();
        newMovie.actors = [];
        actors.forEach((actorName) => {
            newMovie.actors.push({name:actorName});
        });
        fetch("http://localhost:3002/movies", {
            method: "POST",
            headers:{
            'Content-Type':'application/json'
            },
            body: JSON.stringify(newMovie)
        }).then((response) => {
            if (!response.ok) {
                alert(response.status + ": " + response.statusText);
            } else {
                closeModal('add');
                dispatch("addedMovie");
            }
        })
    }

</script>

<Modal title="Add movie" uniqueId="add">
    <form on:submit|preventDefault={addMovie}>
        <div class="form-group row">
            <div class="col">
            <div class="input-group">
                <div class="input-group-prepend">
                <div class="input-group-text">Title</div>
                </div> 
                <input id="text" name="text" type="text" class="form-control" required="required" bind:value={newMovie.title}>
            </div>
            </div>
        </div>
        <div class="form-group row">
            <div class="col">
            <div class="input-group">
                <div class="input-group-prepend">
                <div class="input-group-text">Description</div>
                </div> 
                <input id="text1" name="text1" type="text" class="form-control" required="required" bind:value={newMovie.description}>
            </div>
            </div>
        </div>
        <div class="form-group row">
            <div class="col">
            <div class="input-group">
                <div class="input-group-prepend">
                <div class="input-group-text">Year</div>
                </div> 
                <input id="text2" name="text2" type="number" class="form-control" min=1000 required="required" bind:value={newMovie.year}>
            </div>
            </div>
        </div>
        <div class="form-group row">
            <div class="col">
            <div class="input-group">
                <div class="input-group-prepend">
                <div class="input-group-text">Rating</div>
                </div> 
                <input id="text3" name="text3" type="text" class="form-control" required="required" bind:value={newMovie.rating}>
            </div>
            </div>
        </div>
        <div class="form-group row">
            <div class="col">
            <div class="input-group">
                <div class="input-group-prepend">
                <div class="input-group-text">User score</div>
                </div> 
                <input id="text4" name="text4" type="number" min=0 max=10 class="form-control" required="required" bind:value={newMovie.review.user}> 
                <div class="input-group-append">
                <div class="input-group-text">/10</div>
                </div>
            </div>
            </div>
        </div>
        <div class="form-group row">
            <div class="col">
            <div class="input-group">
                <div class="input-group-prepend">
                <div class="input-group-text">User count</div>
                </div> 
                <input id="text5" name="text5" type="number" min=0 class="form-control" required="required" bind:value={newMovie.review.userCount}>
            </div>
            </div>
        </div>
        <div class="form-group row">
            <div class="col">
            <div class="input-group">
                <div class="input-group-prepend">
                <div class="input-group-text">Meta score</div>
                </div> 
                <input id="text6" name="text6" type="number" min=0 max=100 required="required" class="form-control" bind:value={newMovie.review.metaScore}> 
                <div class="input-group-append">
                <div class="input-group-text">/100</div>
                </div>
            </div>
            </div>
        </div>
        <div class="form-group row">
            <div class="col">
            <div class="input-group">
                <div class="input-group-prepend">
                <div class="input-group-text">IMDB url</div>
                </div> 
                <input id="text7" name="text7" type="text" class="form-control" required="required" bind:value={newMovie.imdb_url}>
            </div>
            </div>
        </div> 
        <MultipleInput title="Languages" bind:data={newMovie.languages} bind:getData={getLanguages}/>
        <MultipleInput title="Actors" bind:data={actors} bind:getData={getActors}/>
        <div class="form-group row">
            <div class="col">
            <button name="submit" type="submit" class="btn btn-primary">Add</button>
            </div>
        </div>
    </form>
</Modal>