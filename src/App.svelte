<script lang="ts">
  import { onMount } from "svelte";

  let movie;

  onMount(() => {
    fetch(
      "https://api.themoviedb.org/3/movie/600583?api_key=09cb613a21480e11c07496d803efc1c7"
    )
      .then((response) => response.json())
      .then((data) => {
        movie = data;
        console.log(data);
      });
  });
</script>

<main>
  {#if movie}
    <h1>{movie?.title}</h1>
    <p>{movie.overview}</p>
    <img src={`https://image.tmdb.org/t/p/w500${movie?.poster_path}`} alt="" />
  {/if}
</main>

<style>
  h1 {
    color: var(--blue-7);
  }
</style>
