<script>
    import { openModal } from "../utils/Modal.svelte";
</script>

<nav class="navbar navbar-dark">
    <img class="navbar-brand" src="https://jeleleforest.nl/img/jelle_s%20logo.svg" alt="logo">
    <h1 class="text-center">My little movie collection</h1>
    <!-- <button class="btn btn-success" on:click={() => openModal("add")}>Add movie</button> -->
</nav>

<style>
    nav {
        background-color: lightblue;
        padding: 1rem;
        border-radius: 5px;
        margin-bottom:2rem;
    }

    img {
        height: clamp(1rem,3rem,4rem);
    }

</style>