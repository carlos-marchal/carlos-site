<script lang="ts">
	import '../app.css';
	let taps = 0;
	$: show = taps > 10;
</script>

{#if show}
	<slot />
{:else}
	<div>Co<span on:click={() => taps++}>m</span>ing soon...</div>
{/if}

<style>
	div {
		margin-top: 50vh;
		font-size: 50px;
		text-align: center;
		transform: translateY(-50%);
		text-transform: uppercase;
	}

	@media (min-width: 800px) {
		div {
			font-size: 150px;
		}
	}
</style>
