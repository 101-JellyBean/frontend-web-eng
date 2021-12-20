<script> 
    import Modal, {openModal,closeModal} from "../utils/Modal.svelte";
    export let actor = {
        id: 0,
        name: "string"
    };

    import MovieSummary from "./MovieSummary.svelte";
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();

    let actorDetails = {movies:[]};
    let actorWiki = {photo:"",discription:""}
    let noActorWiki = {
        photo: "/No-image-found.png",
        discription: "No information found",
        id: 0
    };

    async function openDetails() {
        if (actorWiki.id != actor.id) {
            actorWiki = noActorWiki;
        }
        await fetch("http://localhost:3002" + "/actors/" + actor.id)
        .then(async (response) => actorDetails = await response.json());
        openModal("actor");
        if (actorWiki.id != actor.id) {
            let data = [];
            await fetch("https://en.wikipedia.org/w/api.php?&action=query&generator=search&srsort=relefance&origin=*&gsrnamespace=0&gsrlimit=20&prop=pageimages|extracts&pilimit=max&exintro&exsentences=1&exlimit=max&continue&srwhat=title&pithumbsize=100&format=json&gsrsearch=" + actor.name)
            .then(async (response) => {data = await response.json()});
            let pages = data.query.pages;
            let usefullpages = [];
            for (const property in pages) {
                if (pages[property].title.includes(actor.name)) {
                    usefullpages.push(pages[property]);
                }
            }
            usefullpages.sort((item) => {
                if (item.title == actor.name) {
                    return -1;
                } if (item.title.includes("(actor)")) {
                    return -2;
                } else {
                    return 1;
                }
            });
            actorWiki = {
                photo: usefullpages[0]?.thumbnail?.source ?  usefullpages[0]?.thumbnail?.source : "/No-image-found.png",
                discription: usefullpages[0]?.extract,
                id: actor.id
            };
        }
    }

    function openMovie(id) {
        closeModal("actor");
        dispatch("openMovie",id);
    }

    $: actor.id != 0 && openDetails();


</script>

<Modal uniqueId="actor" title={actor.name}>
    <img src={actorWiki.photo} alt="{actor.name}">
    <!-- @html is not the best solution here because it can enable xss but fine in the example -->
    <p>{@html actorWiki.discription}</p>
    {#each actorDetails.movies as movie}
        <MovieSummary {movie} on:click={() => openMovie(movie.id)}/>
    {/each}
</Modal>