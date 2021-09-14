<script>
	import OpenMPT from './components/OpenMPT.svelte';
  import GameScreenStoryboard from './components/GameScreenStoryboard.svelte';
</script>

<div class="relative">
  <GameScreenStoryboard screen="/opening.jpg" fadeIn />
  <OpenMPT track="/soundtrack/opening.mod"/>
</div>

<style>
  :global(body) {
    background: #090b17;
    font-family: 'Press Start 2P', cursive;
  }
  .relative {
    position: relative;
  }
</style>
