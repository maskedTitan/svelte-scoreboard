<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  export let name;
  export let points;
  const incrementCount = () => (points += 1);
  const decrementCount = () => (points -= 1);
  let showControls = false;
  const toggleControls = () => (showControls = !showControls);

  const handleRemove = () => {
    dispatch("removePlayer", name);
  };
</script>

<style>
  h3 {
    margin-bottom: 10px;
  }
</style>

<div class="card">
  <h1>
    {name}
    <button class="btn btn-sm" on:click={toggleControls}>
      {#if showControls}-{:else}+{/if}
    </button>
  </h1>
  <h3>Points: {points}</h3>
  <button class="btn btn-danger" on:click={handleRemove}>X</button>
  {#if showControls}
    <button class="btn btn-dark" on:click={incrementCount}>increase</button>
    <button class="btn btn-dark" on:click={decrementCount}>decrease</button>
    <input type="number" bind:value={points} />
  {/if}

</div>
