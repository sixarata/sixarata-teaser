<script>
  import MusicOnOffToggle from './MusicOnOffToggle.svelte';
  import StartGameButton from './StartGameButton.svelte';

  export let screen;
  export let fadeIn;
</script>

<div class="poster {fadeIn && 'fade-in'}" style="background-image: url({screen});">
  <MusicOnOffToggle />
  <StartGameButton />
</div>

<style>
  .poster {
    position: relative;
    margin: auto;
    height: 671px;
    width: 1140px;
    background-repeat: no-repeat;
  }
  .fade-in {
    animation: fadeInAnimation ease 20s;
    animation-iteration-count: 1;
    animation-fill-mode: forwards;
  }

  @keyframes fadeInAnimation {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }
</style>
