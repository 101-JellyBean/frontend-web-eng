<script>
    export let actor = {
        id: 0,
        name: "string"
    };

    import Card from "../utils/Card.svelte";
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();

</script>

<Card title={actor.name} on:click={() => dispatch("openActor",actor)}></Card>

