<script>
  import '../app.css';
	import Delegate from '$lib/Delegate.svelte';
  let logoPic = "/images/raspberry-dots-small.png";
  let aaShip = "/images/ship-420.png";
  let delegation = "/images/what-is-cardano-staking.jpg";

  /**
	 * @type {HTMLElement}
	 */
  let piadaSidebar;
  /**
	 * @type {HTMLElement}
	 */
  let delegationModal;

  function w3_open() {
    if (piadaSidebar.style.display === 'block') {
      piadaSidebar.style.display = 'none';
    } else {
      piadaSidebar.style.display = 'block';
    }
    return false;
  }

  function w3_close() {
    piadaSidebar.style.display = "none";
    return false;
  }

  function delegation_modal() {
    delegationModal.style.display = "block";
    return false;
  }

  function delegation_modal_mobile() {
    delegationModal.style.display = "block";
    piadaSidebar.style.display = "none";
    return false;
  }

  function delegation_modal_close() {
    delegationModal.style.display = "none";
    return false;
  }
</script>

<!-- Navbar (sit on top) -->
<div class="w3-top">
    <div class="w3-bar w3-black w3-card" id="piadaNavbar">
      <a href="#home" class="w3-bar-item"><img src={logoPic} alt="PIADA Logo" style="height:60px;"></a>
      <!-- Right-sided navbar links -->
      <div class="w3-right w3-hide-small">
        <a href="#performance" class="w3-bar-item w3-button">PERFORMANCE</a>
        <a href="#about" class="w3-bar-item w3-button">ABOUT US</a>
        <a href="#timeline" class="w3-bar-item w3-button">OUR STORY</a>
        <a href="#spos" class="w3-bar-item w3-button">SPOs</a>
        <a href="#" class="w3-bar-item w3-button" on:click={delegation_modal}>DELEGATION</a>
      </div>
      <!-- Hide right-floated links on small screens and replace them with a menu icon -->
  
      <a href="#" class="w3-bar-item w3-button w3-right w3-hide-large w3-hide-medium" on:click={w3_open}>
        <i class="fa fa-bars"></i>
      </a>
      <div class="w3-modal w3-animate-zoom" on:click={delegation_modal_close} bind:this={delegationModal}>
        <img class="w3-modal-content w3-grayscale-max w3-round w3-mobile" src={delegation} alt="What is Delegation">
      </div>
    </div>
</div>
  
<!-- Sidebar on small screens when clicking the menu icon -->
<nav class="w3-sidebar w3-bar-block w3-black w3-card w3-animate-left w3-hide-medium w3-hide-large" style="display:none" bind:this={piadaSidebar}>
    <a href="#" on:click={w3_close} class="w3-bar-item w3-button w3-large w3-padding-16">Close ×</a>
    <a href="#performance" on:click={w3_close} class="w3-bar-item w3-button">PERFORMANCE</a>
    <a href="#about" on:click={w3_close} class="w3-bar-item w3-button">ABOUT US</a>
    <a href="#timeline" on:click={w3_close} class="w3-bar-item w3-button">OUR STORY</a>
    <a href="#spos" on:click={w3_close} class="w3-bar-item w3-button">SPOs</a>
    <a href="#" class="w3-bar-item w3-button" on:click={delegation_modal_mobile}>DELEGATION</a>
</nav>

<slot />

<!-- Footer -->
<footer class="w3-center w3-black w3-padding-84">
    <Delegate/>
    <div class="w3-xlarge w3-section">
      <span class="p-p3">&#960; &#43; &#8371; &#61; &#8766;</span>
      <a href="https://twitter.com/eastpiada" rel="noreferrer" target="_blank"><i class="fa-brands fa-twitter w3-hover-opacity p-p3"></i></a>
      <a href="https://t.me/piadapool" rel="noreferrer" target="_blank"><i class="fa-brands fa-telegram w3-hover-opacity p-p3"></i></a>
    </div>
    <p>PIADA - ARM'ed Cardano Stake Pool &#169; 2023<br />This website is running in Svelte on a Raspberry Pi <span style="color: #e60000;"><i class="fa-solid fa-heart fa-beat" style="padding-left:5px;--fa-animation-duration: 1.5s;"></i></span></p>
    <p><a href="https://stats.uptimerobot.com/lgx2rF184V" rel="noreferrer" target="_blank">Pool UptimeRobot Stats</a> <i class="fa-solid fa-circle fa-beat w3-text-green" style="padding-left:5px;--fa-animation-duration: 1s;"></i></p>
    
    <p>Pool ID - <a href="https://pooltool.io/pool/b8d8742c7b7b512468448429c776b3b0f824cef460db61aa1d24bc65/awards" target="_blank" rel="noreferrer">b8d8742c7b7b512468448429c776b3b0f824cef460db61aa1d24bc65</a><br />
        Bech32 Pool ID - <a href="https://cexplorer.io/pool/pool1hrv8gtrm0dgjg6zyss5uwa4nkruzfnh5vrdkr2sayj7x2nw6mjc" target="_blank" rel="noreferrer">pool1hrv8gtrm0dgjg6zyss5uwa4nkruzfnh5vrdkr2sayj7x2nw6mjc</a></p>
</footer>