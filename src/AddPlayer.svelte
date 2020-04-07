<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  let player = {
    name: "",
    points: 0
  };
  const handleSubmit = evt => {
    evt.preventDefault();
    dispatch("addPlayer", player);
    player = {
      name: "",
      points: 0
    };
  };
</script>

<form on:submit={handleSubmit} class="grid-3">
  <input type="text" placeholder="Name" bind:value={player.name} />
  <input type="number" placeholder="Points" bind:value={player.points} />
  <input type="submit" value="Add Player" class="btn btn-primary" />
</form>
