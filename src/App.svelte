<script>
	import OpenMPT from './components/OpenMPT.svelte';
  import GameScreenStoryboard from './components/GameScreenStoryboard.svelte';

  const soundtrack = [
    {trackNo: 0, title: 'Opening Screen', url: '/soundtrack/Opening Screen.mod'},
    {trackNo: 1, title: 'First Impression', url: '/soundtrack/First Impression.mod'},
    {trackNo: 2, title: 'Everything Is Going To Be Ok', url: '/soundtrack/Everything Is Going To Be Ok.mod'},
    {trackNo: 3, title: 'Joyride', url: '/soundtrack/Joyride.xm'},
    {trackNo: 4, title: 'The Path Forward', url: '/soundtrack/The Path Forward.xm'},
    {trackNo: 5, title: 'I am the ruler', url: '/soundtrack/I am the ruler.xm'},
    {trackNo: 6, title: 'Bunker Bay Boys', url: '/soundtrack/Bunker Bay Boys.xm'},
    {trackNo: 7, title: 'Edibles Are Kicking In', url: '/soundtrack/Edibles Are Kicking In.mod'},
    {trackNo: 8, title: 'Breakin Out', url: '/soundtrack/Breakin Out.mod'},
    {trackNo: 9, title: 'Flying Through Space', url: '/soundtrack/Flying Through Space.mod'},
    {trackNo: 10, title: 'Fuck You Alien Fucks', url: '/soundtrack/Fuck You Alien Fucks.xm'},
  ];
</script>

<div class="relative">
  <GameScreenStoryboard screen="/opening.jpg" fadeIn />
  <OpenMPT track="/soundtrack/opening.mod"/>
</div>


<div style="margin: 100px 0 0 100px; width: 500px;">
  <h2 style="font-size: 16px; margin-bottom: 20px; color: #3a475d;">Original Game Soundtrack</h2>

  <ul style="padding: 0; ">
    {#each soundtrack as { trackNo, title, url }}
      <li class="flex">
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
    margin: 10px 0;
  }
  .flex {
    display: flex;
  }
  .text-right {
    text-align: right;
  }
  .w-20 {
    width: 3rem;
  }
  .mr-6 {
    margin-right: 1rem;
  }
</style>
