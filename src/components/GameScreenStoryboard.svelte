<script>
  import MusicOnOffToggle from './MusicOnOffToggle.svelte';

  export let screen;
  export let fadeIn;
</script>

<div class="poster {fadeIn && 'fade-in'}" style="background-image: url({screen});">
  <MusicOnOffToggle />
</div>

<style>
  .poster {
    margin: auto;
    min-height: 671px;
    width: 1189px;
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
