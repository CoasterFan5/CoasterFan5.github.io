<script lang="ts">
	// Supports weights 200-800
	import '@fontsource-variable/manrope';
</script>

<slot />

<style lang="scss">
	:global(body) {
		margin: 0;
		height: 100vh;
		width: 100%;
		overflow-y: auto;
		color: #ffffff;
		font-family: manrope, sans-serif;
	}
</style>
