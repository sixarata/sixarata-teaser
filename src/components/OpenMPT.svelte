<svelte:head>
  <script type="text/javascript" src="//cdn.jsdelivr.net/gh/deskjet/chiptune2.js@master/libopenmpt.js"></script>
  <script type="text/javascript" src="//cdn.jsdelivr.net/gh/deskjet/chiptune2.js@master/chiptune2.js"></script>
</svelte:head>

<script>
  import { onMount, afterUpdate } from 'svelte';
  import { musicOn, gameStarted } from '../store';

  export let track;

  $: console.log(track)

  let player;

  $: $musicOn & player?.togglePause();
  $: $gameStarted & player?.togglePause();

  $: {
      let afterLoad = (path, buffer) => player?.play(buffer);
      player?.load(track, afterLoad.bind(this, track));
  }

  const loadTrack = () => {
    window['libopenmpt'] = {};
    libopenmpt.locateFile = (filename) => {
      return "//cdn.jsdelivr.net/gh/deskjet/chiptune2.js@master/" + filename;
    };
    libopenmpt.onRuntimeInitialized = () => {
      player = new ChiptuneJsPlayer(new ChiptuneJsConfig(-1));
      const afterLoad = (path, buffer) => player.play(buffer);
      player.load(track, afterLoad.bind(this, track));
    };
  }

  onMount(() => {
    window['libopenmpt'] = {};
    loadTrack();
  });
</script>
