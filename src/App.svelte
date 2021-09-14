<script>
	import OpenMPT from './components/OpenMPT.svelte';
  import GameScreenStoryboard from './components/GameScreenStoryboard.svelte';
</script>

<div class="relative">
  <GameScreenStoryboard screen="/splash.png" fadeIn />
  <OpenMPT track="/soundtrack/opening.mod"/>
</div>

<style>
  :global(body) {
    background: #090b17;
  }
  .relative {
    position: relative;
  }
</style>
