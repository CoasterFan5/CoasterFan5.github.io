

<script>
	import { onMount } from "svelte";
	let windowHeight;
	let bgPos;
	let scrollPercent = 0;
	let lastUpdate = 0;
	// align the background position of the banner to the scroll position

	let projects = [
		{name: "Project", description: "This is a project", link: "https://google.com"},
		{name: "Project", description: "This is a project", link: "https://google.com"},
		{name: "Project", description: "This is a project", link: "https://google.com"},
	]
	
	$: scrollPercent = scroll / windowHeight * 100;
	$: bgPos = Math.max(0, 100 - scrollPercent);

	let oldRandomCharGen =() => {
		let chars = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";
		let result = "";
		for (let i = 0; i < 20000; i++) {
			result += chars.charAt(Math.floor(Math.random() * chars.length));
		}
		return result;
	}
	let outdatedSupport = oldRandomCharGen();

	console.log(crypto)

	let dec2hex = (dec) => {
		return dec.toString(16).padStart(2, "0");
	}

	let LargeRandomCharGen = (window) => {
		if(!crypto || !crypto.getRandomValues) {
			return outdatedSupport;
		}
		console.log(crypto)
		let array = new Uint32Array(1500);
		let val = crypto.getRandomValues(array);
		return Array.from(val, dec2hex).join('')
	
	
	}
	
	let bigRandomString = oldRandomCharGen();
	let scroll = (event) => {
		//only update bg if it has been 25ms since last update to prevent lag
		let pos = window.scrollY;
		if(pos > windowHeight) {
			return;
		}
		if(Date.now() - lastUpdate > 25) {
			lastUpdate = Date.now();
			bigRandomString = LargeRandomCharGen(window);
		}
		
	}

	
</script>


<svelte:window bind:innerHeight={windowHeight} on:scroll={scroll}/>
<div class="wrap">
	<div class="banner" >
		<div class="bannerBG">
			{bigRandomString}
		</div>
		<div class="bannerContent">
			<h1 class="title">Hello!</h1>
			<h3>(This website is still under construction)</h3>
		</div>
	</div>
	<div class="about">
		<h1 id="about">About Me!</h1>
		<p>I am known as CoasterFan5 and I do the cool coding thing. I am primarly a web developer using Javascript, Typescript, Svelte. I also use Java, C#, C++, and Rust for less web focused projects.</p>
		
	</div>

	<div class="projects">
		<div class="toolbar">
			<h1>Projects</h1>
			{#each projects as project}
				<div class="project">

				</div>
			{/each}
		</div>
	</div>
</div>



<style>
	
	.banner {
		height: 100vh;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		z-index: 1;
		background: rgba(0, 0, 0, 0.5);
		color: white;
		
	}
	.bannerBG {
		background: rgb(0, 42, 179);
		height: 100%;
		width: 100%;
		position: absolute;
		top: 0px;
		left: 0px;
		z-index: -1;
		color: white;
		overflow-wrap: break-word;
		font-family: 'Courier New', Courier, monospace;
		overflow: hidden;
	}
	.bannerContent {
		width: 100%;
		height: 100%;
		backdrop-filter: blur(1px);
		text-align: center;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}
	.bannerContent h1 {
		font-size: 6em;
		margin: 0px;
		margin: 5px;
	}
	.bannerContent h3 {
		font-size: 1em;
		margin: 0px;
		margin: 10px;
	}
	.about {
		padding: 0px 10%;
		box-sizing: border-box;
		display: flex;
		flex-direction: column;
	}
	.projects {
		padding: 0px 10%;
		box-sizing: border-box;
		display: flex;
		flex-direction: column;
	}
</style>