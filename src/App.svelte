<script>
	import OpenMPT from './components/OpenMPT.svelte';
  import GameScreenStoryboard from './components/GameScreenStoryboard.svelte';

  $: selectedTrack = '/soundtrack/Opening-Screen.mod';

  let showGame = false;

  const soundtrack = [
    {active: true, trackNo: 0, title: 'Opening Screen', url: '/soundtrack/Opening-Screen.mod'},
    {active: false, trackNo: 1, title: 'First Impression', url: '/soundtrack/First-Impression.mod'},
    {active: false, trackNo: 2, title: 'Everything Is Going To Be Ok', url: '/soundtrack/Everything-Is-Going-To-Be-Ok.mod'},
    {active: false, trackNo: 3, title: 'Joyride', url: '/soundtrack/Joyride.xm'},
    {active: false, trackNo: 4, title: 'The Path Forward', url: '/soundtrack/The-Path-Forward.xm'},
    {active: false, trackNo: 5, title: 'I am the ruler', url: '/soundtrack/I-am-the-ruler.xm'},
    {active: false, trackNo: 6, title: 'Bunker Bay Boys', url: '/soundtrack/Bunker-Bay-Boys.xm'},
    {active: false, trackNo: 7, title: 'Edibles Are Kicking In', url: '/soundtrack/Edibles-Are-Kicking-In.mod'},
    {active: false, trackNo: 8, title: 'Breakin Out', url: '/soundtrack/Breakin-Out.mod'},
    {active: false, trackNo: 9, title: 'Flying Through Space', url: '/soundtrack/Flying-Through-Space.mod'},
    {active: false, trackNo: 10, title: 'Fuck You Alien Fucks', url: '/soundtrack/Fuck-You-Alien-Fucks.xm'},
    {active: false, trackNo: 11, title: 'Forever With You', url: '/soundtrack/forever-in-this-moment-with-you.xm'},
  ];
</script>

{#if showGame}
<div class="relative">
  <GameScreenStoryboard screen="/opening.jpg" fadeIn />
  <OpenMPT track={selectedTrack}/>
</div>
{:else}
<div class="relative text-center">
  <button on:click={() => showGame = true}>LOAD GAME</button>
  </div>
{/if}


<div style="margin: 100px auto 0 auto; padding-left: 100px; width: 500px; width: 1189px;">
  <h2 style="font-size: 16px; margin-bottom: 20px; color: #3a475d;">Original Game Soundtrack</h2>
  <ul style="padding: 0; color: #999999; cursor: pointer">
    {#each soundtrack as { trackNo, title, url }}
      <li class="flex" on:click={() => selectedTrack = url }>
        <div class="w-20 mr-6 text-right">{trackNo}</div>
        <div>{title}</div>
      </li>
    {/each}
  </ul>
</div>

<style>
  :global(body) {
    background: #090b17;
    font-family: 'Press Start 2P', cursive;
    color: white;
  }
  .relative {
    position: relative;
  }
  ul {
    font-size: 0.7rem;
  }
  li {
    padding: 5px 0;
    transition: all 0.1s;
  }
  li:hover {
    color: #f66586;
  }
  .flex {
    display: flex;
  }
  .text-right {
    text-align: right;
  }
  .text-center {
    text-align: center;
  }
  .w-20 {
    width: 3rem;
  }
  .mr-6 {
    margin-right: 1rem;
  }
</style>
