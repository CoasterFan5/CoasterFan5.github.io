
<div class="sidebarwrap">
	<a href="./">CoasterFan5</a>
	<hr>
	<a href="./about">About</a>
	<a href="./projects">Projects</a>
	<a href="./contact">Contact</a>
</div>




<style>
	.sidebarwrap {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		height: 100vh;
		width: 200px;
		text-align: center;
		background: rgba(13, 13, 13, 1);
	}
	.sidebarwrap hr {
		width: 70%;
		border: none;
		border-bottom: 1px solid rgba(228, 228, 228, 0.1);
		
	}
	.sidebarwrap a {
		text-decoration: none;
		background-image: linear-gradient(90deg, #0581E8 75%, white 50%);
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
		background-image: linear-gradient(90deg, #0581E8 75%, white 50%);
		background-position: 0%;
		background-size: 400%;
		
		color: transparent;
		transition: background-position 1s;
	}
</style>