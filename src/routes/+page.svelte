<script>
	import Sidebar from "$lib/sidebar.svelte";
	import { positions } from "$lib/positions.js";
	import { onMount } from "svelte";

	let steps = 100;
	let posCopy = JSON.parse(JSON.stringify(positions));
	let dots = posCopy["name"];
	let canvas;
	let canvasHeight = 0;
	let canvasWidth = 0;
	let centerx = 0;
	let centery = 0;
	let squareRadius = 0;
	let fadingTo = "name";
	let ctx;
	let frameRate = 60;

	let rgbs = 3;
	let r = 0;
	let g = 255;
	let b = 255;

	$: trueCanvasHeight = canvasHeight;
	$: trueCanvasWidth = canvasWidth;
	$: squareRadius = Math.floor(Math.min(canvasWidth/2, canvasHeight/2));
	$: centerx = Math.floor(canvasWidth/2);
	$: centery = Math.floor(canvasHeight/2);
	

	$: console.log(canvasHeight, canvasWidth)
	

	onMount(() => {
		setInterval(() => {
			fadeCanvas();
		}, 1000/60)
		if(!canvas) return;
		ctx = canvas.getContext("2d");
	})
	
	let fadeCanvas = () => {

		//fade colors
		let rgbsfactor = 0.2;
		switch(rgbs) {
			case 0: //255, i, 0
				g += rgbsfactor;
				if(g >= 255) {
					rgbs++;
				}
				break;
			case 1: //d, 255, 0
				r -= rgbsfactor;
				if(r <= 0) {
					rgbs++;
				}
				break;
			case 2: //0, 255, i
				b += rgbsfactor;
				if(b >= 255) {
					rgbs++;
				}
				break;
			case 3: //0, d, 255
				g -= rgbsfactor;
				if(g <= 0) {
					rgbs++;
				}
				break;
			case 4: //i, 0, 255
				r += rgbsfactor;
				if(r >= 255) {
					rgbs++;
				}
				break;
			case 5: //255, 0, d
				b -= rgbsfactor;
				if(b <= 0) {
					rgbs = 0;
				}
				break;

		}


		if(!canvas || !ctx) return;
		//find a nice square centered on the canvas
		
		
		canvas.height = canvasHeight;
		canvas.width = canvasWidth;
		let bottomx = centerx-squareRadius;
		let topx = centerx+squareRadius;
		let bottomy = centery-squareRadius;
		let topy = centery+squareRadius;
		let xstep = (topx-bottomx)/100;
		let ystep = (topy-bottomy)/100;
		dots.forEach((dot, index) => {
			//get the dots position and the position it should be in
			
			if(!positions[fadingTo][index]) {
				let newDot = {x: 0, y: 0};
				newDot.x = Math.floor(Math.random()*100);
				newDot.y = Math.floor(Math.random()*100);
				newDot.opacity = 0;
				positions[fadingTo].push(newDot);
			}
			
			dot.opacity += (positions[fadingTo][index].opacity - dot.opacity)/10;
			dot.x += ((positions[fadingTo][index].x) - dot.x)/12;
			dot.y += ((positions[fadingTo][index].y) - dot.y)/12;
			//add variation of 5-10 px to the position
			
			//draw the dot
			ctx.fillStyle = `rgba(${r}, ${g}, ${b}, ${dot.opacity})`;
			ctx.global = dot.opacity;
			let dotx = dot.x * xstep + bottomx + Math.floor(Math.random());
			let doty = dot.y * ystep + bottomy + Math.floor(Math.random());;
			ctx.moveTo(dotx, doty);
			ctx.arc(dotx, doty, 5, 0, 2*Math.PI);
		})
		ctx.fill();
	}

	let setFadingTo = (name) => {
		console.log(name)
		fadingTo = name;
	}
</script>



<div class="wrap" style="--color: rgb({r}, {g}, {b})">
	<div class="sidebarwrap">
		<a href="./" on:mouseenter={() => setFadingTo("name")}>CoasterFan5</a>
		<hr>
		<a href="./about" on:mouseenter={() => setFadingTo("about")}>About</a>
		<a href="./projects" on:mouseenter={() => setFadingTo("projects")}>Projects</a>
		<a href="./contact" on:mouseenter={() => setFadingTo("contact")}>Contact</a>
	</div>
	<div class="dotHolder" bind:clientHeight={canvasHeight} bind:clientWidth={canvasWidth}>
		<canvas bind:this={canvas}> 
			
	</div>
</div>



<style>
	
	.wrap {
		display: flex;
		width: 100vw;
		height: 100vh;
		flex-direction: row;
	}
	.dotHolder {
		width: 100%;
		flex-grow: 2;
		height: 100%;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		background: rgb(29, 29, 29);
	}
	.sidebarwrap {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		height: 100vh;
		width: 200px;
		text-align: center;
		background: rgba(0, 0, 0, 0.2);
	}
	.sidebarwrap hr {
		width: 70%;
		border: none;
		border-bottom: 1px solid rgba(228, 228, 228, 0.1);
		
	}
	.sidebarwrap a {
		text-decoration: none;
		background-image: linear-gradient(90deg, var(--color) 75%, white 50%);
		background-position: 100%;
		background-size: 400%;
		background-clip: text;
		-webkit-background-clip: text;
		color: transparent;
		transition: background-position 0.5s;
		font-size: 1.5rem;

	}
	.sidebarwrap a:hover {
		text-decoration: none;
		background-image: linear-gradient(90deg, var(--color) 75%, white 50%);
		background-position: 0%;
		background-size: 400%;
		
		color: transparent;
		transition: background-position 1s;
	}
</style>