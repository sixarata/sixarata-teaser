<svelte:head>
  <script type="text/javascript" src="//cdn.jsdelivr.net/gh/deskjet/chiptune2.js@master/libopenmpt.js"></script>
  <script type="text/javascript" src="//cdn.jsdelivr.net/gh/deskjet/chiptune2.js@master/chiptune2.js"></script>
</svelte:head>

<script>
  import { onMount } from 'svelte';
  import { musicOn } from '../store';

  export let track;

  let player;

  $: $musicOn & player?.togglePause();

  onMount(() => {
    window['libopenmpt'] = {};
    libopenmpt.onRuntimeInitialized = () => {
      const init = () => player = new ChiptuneJsPlayer(new ChiptuneJsConfig(-1));
      const afterLoad = (path, buffer) => player.play(buffer);
      init() & player.load(track, afterLoad.bind(this, track))
    };
  });
</script>