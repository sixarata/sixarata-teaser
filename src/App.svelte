<script>
	import OpenMPT from './components/OpenMPT.svelte';
  import GameScreenStoryboard from './components/GameScreenStoryboard.svelte';

  import { fade, slide, fly } from 'svelte/transition';

  $: selectedTrack = '/soundtrack/Opening-Screen.mod';

  let showGame = false;

  const soundtrack = [
    {active: true, trackNo: 0, title: 'Opening Screen', url: '/soundtrack/Opening-Screen.mod'},
    {active: false, trackNo: 1, title: 'First Impression', url: '/soundtrack/First-Impression.mod'},
    {active: false, trackNo: 2, title: 'It\'s Going To Be Ok', url: '/soundtrack/Everything-Is-Going-To-Be-Ok.mod'},
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

  const soundtrack2 = [
    {active: true, trackNo: 12, title: 'Signal Detected', url: '/soundtrack2/00_-_Signal_Detected.xm'},
    {active: false, trackNo: 13, title: 'Where Have You Been', url: '/soundtrack2/01_-_lipton.xm'},
    {active: false, trackNo: 14, title: 'City Slicker', url: '/soundtrack2/02_-_City_Slicker.mod'},
    {active: false, trackNo: 15, title: 'Light-years for You', url: '/soundtrack2/03_-_Lightyears_for_You.xm'},
    {active: false, trackNo: 16, title: 'Last Cruise on Earth', url: '/soundtrack2/04_-_Last_Cruise_on_Earth.mod'},
    {active: false, trackNo: 17, title: 'Lock \'n Load', url: '/soundtrack2/04_-_Lock_n_Load.xm'},
    {active: false, trackNo: 18, title: 'Stay Right There', url: '/soundtrack2/04_-_Stay_Right_There.xm'},
    {active: false, trackNo: 19, title: 'You Feel Me Tho', url: '/soundtrack2/05_-_You_feel_me_tho.xm'},
    {active: false, trackNo: 20, title: 'Killing Aliens', url: '/soundtrack2/07_-_Killing_Aliens.xm'},
    {active: false, trackNo: 21, title: 'Groove Alley', url: '/soundtrack2/08_-_Groove_Alley.mod'},
    {active: false, trackNo: 22, title: 'Spinwheel', url: '/soundtrack2/13_-_Spinwheel.xm'},
    {active: false, trackNo: 23, title: 'Earthly Worship', url: '/soundtrack2/09_-_Earthly_Worship.xm'},
    {active: false, trackNo: 24, title: 'Strip Club Basement', url: '/soundtrack2/11_-_Strip_Club_Basement.mod'},
    {active: false, trackNo: 25, title: 'Shadow Movements', url: '/soundtrack2/12_-_Shadow_Movements.mod'},
    {active: false, trackNo: 26, title: 'In My Arms', url: '/soundtrack2/14_-_In_My_Arms.xm'},
  ];
</script>

{#if showGame}
<div class="relative" style="max-width: 1140px; margin: 0 auto; z-index: 2;">
  <div in:fade|global={{ duration: 6000, delay: 1600}} style="position: absolute; bottom: 30px; right: 30px; z-index: 1000;">
    <h2 style="font-size: 16px; margin-bottom: 20px; color: #3a475d;">Side A</h2>
    <ul style="padding: 0; color: #999999; cursor: pointer; margin-bottom: 30px;  text-shadow: 0 0 10px #43907e;">
      {#each soundtrack as { trackNo, title, url }}
        <li class="flex" on:click={() => selectedTrack = url }>
          <div class="w-20 mr-6 text-right">{trackNo}</div>
          <div>{title}</div>
        </li>
      {/each}
    </ul>
  </div>
  <GameScreenStoryboard screen="/opening.jpg" fadeIn />
  <OpenMPT track={selectedTrack}/>
</div>

<div in:fade={{ duration: 7000, delay: 3500}} style=" display: flex;  max-width: 1140px; width: 100%; margin: 10px auto; z-index: 1;">
  <div style="position: relative; width: 100%;">
    <div in:fade|global={{ duration: 2000, delay: 4500}} style="position: absolute; top: 50px; left: 70px;">
      <h2 style="font-size: 16px; margin-bottom: 20px; color: #3a475d;">Side B</h2>
      <ul style="padding: 0; color: #f3f3f3; cursor: pointer; text-shadow: 0 0 10px #f66586a0;">
        {#each soundtrack2 as { trackNo, title, url }}
          <li class="flex" on:click={() => selectedTrack = url }>
            <div class="w-20 mr-6 text-right">{trackNo}</div>
            <div>{title}</div>
          </li>
        {/each}
      </ul>
    </div>
    <img src="/sixarataVol2.jpg" alt="" style="max-width: 1140px; width: 100%;"/>
  </div>
</div>
{:else}
<div class="relative text-center" style="height: 100vh; display: flex; align-items: center; justify-content: center;">
  <button on:click={() => showGame = true} style="font-size: 2rem; padding: 1rem 2rem; background: transparent; color: #fff; border: none; cursor: pointer; border-radius: 0.5rem; text-shadow: 0 0 10px #f66586a0; font-family: 'Press Start 2P', cursive;">LOAD GAME</button>
  </div>
{/if}


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
