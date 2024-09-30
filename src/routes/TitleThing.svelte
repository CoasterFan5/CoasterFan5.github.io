<script lang="ts">
	export let value = 'CoasterFan5';
	let arr = value.split('');
</script>

<div>
	<h2>
		{value}
	</h2>
</div>

<style lang="scss">
	h2 {
		animation: g 15s ease-in-out infinite;
	}

	@keyframes g {
		0% {
			letter-spacing: 0rem;
		}
		50% {
			letter-spacing: 0.5rem;
		}
		100% {
			letter-spacing: 0rem;
		}
	}

	h2 {
		margin: 0px;
		font-size: 2.5rem;
		font-weight: 500;
	}
</style>
