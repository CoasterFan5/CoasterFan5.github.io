
<script>
	import Sidebar from "$lib/Sidebar.svelte";
</script>

<div class="wrap">
	<div class="secondWrap">
		<Sidebar/>
		<div class="content">
			<slot>

			</slot>
		</div>
	</div>
</div>


<style>
	:global(body) {
		margin: 0;
		padding: 0;
		font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
	}
	.content {
		width: 100%;
		height: 100%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	.wrap {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		height: 100vh;
		width: 100%;
		background-image: url("/bg.svg");
		background-size: cover;
		background-position: center;
	}
	.secondWrap {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		height: 100vh;
		width: 100%;
		background: rgba(13, 13, 13, 0.5);
		backdrop-filter: blur(200px);
		background-size: cover;
		background-position: center;	
	}
</style>