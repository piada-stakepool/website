
<script>
	import Delegate from "$lib/Delegate.svelte";
  let aaShip = "/images/ship-420.png";
</script>

<header class="rimage w3-display-container" id="home">
    <div class="w3-display-left w3-text-white" style="padding:48px">
      <h1 class="w3-jumbo w3-hide-small">Delegate with PIADA</h1>
      <h1 class="w3-xxlarge w3-hide-large w3-hide-medium">Delegate with PIADA</h1>
      <h4 class="w3-large">
        Armada Alliance OGs forging Cardano blockchain rewards on efficient hardware since mainnet epoch 255.
      </h4>
      <h4 class="w3-large">
        Non-custodial, direct delegation. You always have control of your Cardano assets.
      </h4>
      <Delegate/>
    </div>

    <div class="w3-container w3-display-bottomleft w3-xlarge w3-text-white" style="padding:24px 48px">
      <div class="w3-row">
        <span class="w3-xxlarge p-p3">&#960; &#43; &#8371; &#61; &#8766;</span>
        <a href="https://twitter.com/eastpiada" rel="noreferrer" target="_blank"><i class="fa-brands fa-twitter w3-hover-opacity w3-xxlarge p-p3"></i></a>
        <a href="https://t.me/piadapool" rel="noreferrer" target="_blank"><i class="fa-brands fa-telegram w3-hover-opacity w3-xxlarge p-p3"></i></a>
      </div>
    </div>
</header>

<style>
  h1,h4 {text-shadow:2px 2px 4px #000;}
  .rimage {
    background-position: center;
    background-size: cover;
    background-attachment: fixed;
    background-repeat: no-repeat;
    background-image: url('/images/top-page-bkg.webp');
    min-height: 100%;
  }
</style>