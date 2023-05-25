<div class="wrap">
	<div class="card">
		<h1>IMCtools</h1>
		<hr>
		<p>IMC Tools is a calculator made in Svelte for a Minecraft server.</p>
	</div>

	<div class="card">
		<h1>Cosmica</h1>
		<hr>
		<p>Cosmica is a still in-development web proxy built in Svelte.</p>
	</div>

	<div class="card">
		<h1>Coaster Services</h1>
		<hr>
		<p>The main website for Coaster Services, integrates logins, external authentications, and more! Built with MongoDB and Svelte.</p>
	</div>
</div>

<style>
	.wrap {
		display: flex;
		flex-direction: column;
		grid-gap: 10px;
		justify-content: start;
		height: 100vh;
		width: 100%;
	}

	.card {
		background: rgba(13, 13, 13, 0.5);
		backdrop-filter: blur(100px);
		min-width: 200px;
		margin: 10px 5%;
		padding: 1rem 2rem; 
		border-radius: 1rem;
		color: white;
		display: flex;
		flex-direction: row;
		align-items: center;
	}

	.card h1 {
		font-size: 2rem;
		font-weight: 300;
		flex-wrap: nowrap;
	}
	.card hr {
		font-size: 1rem;
		font-weight: 300;
		margin-left: 10px;
		height: 90%;
		width: 1px;
	}
	.card p {
		width: 200%;
		font-size: 1rem;
		font-weight: 300;
		margin-left: 10px;
	}
</style>