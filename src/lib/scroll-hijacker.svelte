<script lang="ts">
	import { createEventDispatcher } from 'svelte';
	export let height: string;
	export let threshold = 0;
	let scrollY: number;
	let section: HTMLElement | undefined;
	let lastProgress: number | undefined;
	const dispatch = createEventDispatcher();
	let progress = 0;
	function handleScroll() {
		if (section === undefined) {
			return;
		}
		const top = scrollY - section.offsetTop;
		const height = section.offsetHeight - window.innerHeight;
		const trueRatio = top / height;
		const paddedRatio = (trueRatio - threshold) / (1 - threshold * 2);
		progress = Math.min(1, Math.max(0, paddedRatio));
		if (progress === lastProgress) {
			return;
		}
		lastProgress = progress;
		dispatch('progress', progress);
	}
	$: [scrollY, threshold], handleScroll();
</script>

<svelte:window bind:scrollY />
<section bind:this={section} style:height style:--progress={progress}><div><slot /></div></section>

<style>
	section {
		position: relative;
	}

	div {
		position: sticky;
		overflow: hidden;
		top: 0;
		height: 100vh;
		display: grid;
		place-items: center;
	}
</style>
