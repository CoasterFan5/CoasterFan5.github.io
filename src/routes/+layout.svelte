<script lang="ts">
	import '@fontsource-variable/manrope';
	import type { Snippet } from 'svelte';

	let {
		children
	}: {
		children: Snippet<[]>;
	} = $props();
</script>

<title>CoasterFan5</title>
{@render children?.()}

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
