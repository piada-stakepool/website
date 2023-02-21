<script>
    /*
	let getPoolUptime = (async () => {
		const res = await fetch(
			'https://api.uptimerobot.com/v2/getMonitors?format=json&api_key=ur1967275-b3b281dc8596ed10791ab890', { method: 'POST' }
		);
		return await res.json();
	})();
    */
    import perfData from '$lib/data/poolData.json';
    import sliderData from '$lib/data/carouselData.json';
    import Grid from "gridjs-svelte"
    import Carousel from "svelte-carousel";
    import { browser } from '$app/environment';

    /**
	 * @type {Carousel}
	 */
    let carousel; // for calling methods of the carousel instance
    const handleNextClick = () => {carousel.goToNext()}
    const data = [perfData]
    const slides = sliderData

</script>


<!-- <Grid
    data={data}
	sort
	search
	pagination={{ enabled: true, limit: 3 }}
    columns={[
        { name: "total_delegated", sort: true },
        { name: "pledge", sort: true },
        { name: "block_count", sort: true },
        { name: "life_time_ros", sort: true },
        { name: "pool_fee", sort: true },
        { name: "delegate_rewards", sort: true },
    ]}
    style={{
        table: {
            border: "1px solid #ccc",
            "border-collapse": "collapse",
            "border-spacing": 0,
            "font-size": "14px",
            "text-align": "left",
            width: "100%",
        },
        th: {
            "background-color": "#4285af",
            color: "#fff",
            padding: "10px",
        },
        td: {
            padding: "10px",
            "vertical-align": "top",
            "border-bottom": "1px solid #ccc",
        },
    }}
/> -->

<!-- <style global> 
    @import "https://cdn.jsdelivr.net/npm/gridjs/dist/theme/mermaid.min.css";
</style> -->

<div class="w3-container" id="performance" style="background-color:#4285af;">
    <div class="w3-row w3-center w3-text-white" style="padding:84px 0px">
        <div class="w3-col l2 m12 s12 w3-padding-32 w3-large">
            <span class="w3-xxlarge">{perfData.total_delegated}+</span>&#8371;<br>
            Pool Delegation
        </div>
        <div class="w3-col l2 m12 w3-mobile w3-padding-32 w3-large">
            <span class="w3-xxlarge">{perfData.pledge}</span>&#8371;<br>
            Pool Pledge
        </div>
        <div class="w3-col l2 m12 w3-mobile w3-padding-32 w3-large">
            <span class="w3-xxlarge">{perfData.block_count}</span><br>
            Lifetime Pool Blocks
        </div>
        <div class="w3-col l2 m12 w3-mobile w3-padding-32 w3-large">
            <span class="w3-xxlarge">{perfData.life_time_ros}%</span><br>
            Lifetime Return on Delegation
        </div>
        <div class="w3-col l2 m12 w3-mobile w3-padding-32 w3-large">
            <span class="w3-xxlarge">{perfData.pool_fee}%</span><br>
            Low Variable Pool Fee
        </div>
        <div class="w3-col l2 m12 w3-mobile w3-padding-32 w3-large">
            <span class="w3-xxlarge">{perfData.delegate_rewards}</span>&#8371;<br>
            Lifetime Rewards to Delegates
        </div>
    </div>



    <!-- OLD SLIDER CODE-->
    <!-- {#each sliderData as sd}
    <div class="w3-row w3-center w3-black w3-round-xlarge" style="padding:84px 0px;margin-bottom:16px;">
        <div class="w3-col w3-mobile">
            <a href={sd.imgHref} rel="noreferrer" target="_blank"><img src={sd.imgSrc} class="w3-image carousel-logo" alt={sd.imgAlt} width={sd.imgWidth}></a>
            <p class="carousel w3-xlarge w3-text-white">{@html sd.description}</p>
        </div>
    </div>
    {/each} -->

{#if browser}
  <Carousel
    bind:this={carousel}
    autoplay
    autoplayDuration={5000}
    pauseOnFocus
    let:loaded >
    {#each slides as slide, imageIndex (slide)}
      <div class="w3-row w3-center w3-black w3-round-xlarge" style="padding:84px 0px;margin-bottom:16px;">
        <div class="w3-col w3-mobile">
            {#if loaded.includes(imageIndex)}
            <a href={slide.imgHref} rel="noreferrer" target="_blank"><img src={slide.imgSrc} class="w3-image carousel-logo" alt={slide.imgAlt} width={slide.imgWidth}></a>
            <p class="carousel w3-xlarge w3-text-white">{@html slide.description}</p>
            {/if}
        </div>
    </div>
    {/each}
  </Carousel>
{/if}


<!--
    <div class="w3-row w3-center w3-black w3-round-xlarge" style="padding:84px 0px;margin-bottom:16px;">
        <div class="w3-row-padding w3-center" style="margin-top:84px!important">
            {#await getPoolUptime}
            <div class="w3-center w3-padding-32">
                <p class="w3-large">Loading Relay Statuses</p>
            </div>
            {:then data}
                {#if data.stat === "ok"}
                    {#if data.monitors[0].status === 2}
                    <div class="w3-third">
                        <i class="fa-solid fa-heart-circle-check fa-beat-fade w3-margin-bottom w3-jumbo w3-text-green" style="--fa-animation-duration: 2s; --fa-beat-fade-opacity: 0.67; --fa-beat-fade-scale: 1.055;"></i>
                        <p class="w3-large">Relay 1 is doing just fine</p>
                    </div>
                    {:else}
                    <div class="w3-third">
                        <i class="fa-solid fa-heart-crack w3-margin-bottom w3-jumbo w3-text-red"></i>
                        <p class="w3-large">Relay 1 is undergoing maintenance</p>
                    </div>
                    {/if}
                    <div class="w3-third w3-padding-32">
                        <i class="fa-solid fa-circle w3-margin-bottom w3-tiny w3-text-green"></i><span class="w3-xlarge" style="padding-left:5px;"><a href="https://stats.uptimerobot.com/lgx2rF184V" rel="no-referrer" target="_blank">UptimeRobot</a></span>
                    </div>
                    {#if data.monitors[1].status === 2}
                    <div class="w3-third">
                        <i class="fa-solid fa-heart-circle-check fa-beat-fade w3-margin-bottom w3-jumbo w3-text-green"></i>
                        <p class="w3-large">Relay 2 is doing just fine</p>
                    </div>
                    {:else}
                    <div class="w3-third">
                        <i class="fa-solid fa-heart-crack w3-margin-bottom w3-jumbo w3-text-red"></i>
                        <p class="w3-large">Relay 2 is undergoing maintenance</p>
                    </div>
                    {/if}
                {:else}
                <div class="w3-center w3-padding-32">
                    <p class="w3-large">No UptimeRobot API Available</p>
                </div>
                {/if}
            {:catch error}
            <div class="w3-center w3-padding-32">
                <p class="w3-large">No UptimeRobot API Available</p>
            </div>
            {/await}
        </div>
    </div>
    -->
</div>

<!-- <style>
.w3-col {text-shadow:1px 1px 4px #000;}
.w3-col .carousel {text-shadow:1px 1px 0 #131522;}
.carousel-logo {
    margin-bottom: 13px;
    padding:10px;
}
</style> -->
