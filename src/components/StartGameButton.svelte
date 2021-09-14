<script>
	import { gameStarted } from './../store.js';
</script>

<button on:mousedown={() => gameStarted.set(!$gameStarted)}>
  {#if !$gameStarted}
    Start Game
  {:else}
    Not Yet
  {/if}
</button>

<style>
  button {
    position: absolute;
    bottom: 50px;
    left: 76px;
    font-family: 'Press Start 2P', cursive;
    font-size: 20px;
    background: rgba(255, 255, 255, 0.1);
    color: #fff;
    border: none;
    padding: 13px 20px;
    border-radius: 5px;
    text-transform: uppercase;
    cursor: pointer;
    z-index: 999;
    transition: background-color 0.5s ease;
  }
  button:hover {
    background: rgba(89, 192, 161, 0.815)  }
</style>
