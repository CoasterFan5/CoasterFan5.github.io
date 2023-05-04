<script>
	import Sidebar from '$lib/Sidebar.svelte'
</script>

<div class="wrap">
	<Sidebar/>
	<div class="content">
		<slot/>
	</div>
	
</div>

<style>
	:global(body) {
		margin: 0;
		padding: 0;
		font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
		background: rgb(15, 15, 15);
		color: rgb(228, 228, 228);
	}
	.wrap {
		display: flex;
		width: 100vw;
		height: 100vh;
		flex-direction: row;
	}
	.content {
		width: 100%;
		flex-grow: 2;
		height: 100%;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: start;
	}
</style>