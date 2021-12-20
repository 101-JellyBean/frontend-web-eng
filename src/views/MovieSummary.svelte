<script>
    import Card from "../utils/Card.svelte";
    export let movie = {
        "id": 0,
        "title": "string",
        "year": 0,
        "rating": "string"
  }
</script>

<Card title={movie.title} on:click>
    <p>Rating: {movie.rating} Year: {movie.year}</p>
</Card>