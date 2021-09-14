<script>
  import { musicOn } from '../store';
  import GoUnmute from 'svelte-icons/go/GoUnmute.svelte';
  import GoMute from 'svelte-icons/go/GoMute.svelte';
</script>

<button on:mousedown={() => musicOn.set(!$musicOn)}>
  {#if $musicOn}
    <GoUnmute />
  {:else}
    <GoMute />
  {/if}
</button>

<style>
  button {
    position: absolute;
    right: 10px;
    top: 20px;
    width: 50px;
    height: 50px;
    padding: 10px;
    color: rgba(255, 255, 255, 0.5);
    border-radius: 100%;
    border: 1px solid rgba(255, 255, 255, 0.3);
    background: rgba(255,255,255,0.1);
  }
</style>
