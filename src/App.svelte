<script>
  import Navbar from "./Navbar.svelte";
  import Player from "./Player.svelte";
  import AddPlayer from "./AddPlayer.svelte";

  let players = [
    {
      name: "Harsha",
      points: 500
    },
    {
      name: "Sam",
      points: 600
    },
    {
      name: "Martin",
      points: 443
    }
  ];

  const addPlayer = evt => {
    const newPlayer = evt.detail;
    players = [...players, newPlayer];
  };

  const removePlayer = evt => {
    const updatedPlayers = players.filter(player => player.name !== evt.detail);
    players = updatedPlayers;
  };
</script>

<Navbar />
<div class="container">
  <AddPlayer on:addPlayer={addPlayer} />

  {#if players.length === 0}
    <p>No Players</p>
  {:else}
    {#each players as player}
      <Player
        name={player.name}
        points={player.points}
        on:removePlayer={removePlayer} />
    {/each}
  {/if}
</div>
