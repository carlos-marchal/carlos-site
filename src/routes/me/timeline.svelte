<script lang="ts">
	import ScrollHijacker from '$lib/scroll-hijacker.svelte';

	const start = 2014;
	const end = 2022;
	const years = Array.from({ length: end - start + 1 }).map((_, index) => index + start);
	const data = [
		{
			start: 2014,
			content: ['studied', { em: 'Computer Science' }, 'at', 'Universitat Politècnina de Catalunya']
		},
		{
			start: 2018,
			content: ['worked as', { em: 'Freelance' }]
		},
		{
			start: 2020,
			content: ['founded', { em: 'haddock' }, 'as', 'CTO and Tech Lead']
		},
		{
			start: 2021,
			content: ['worked at', { em: 'haddock' }, 'as', 'CTO and Tech Lead']
		}
	];
	let scrollProgress = 0;
	$: timelineProgress = (end - start) * scrollProgress;
	$: year = Math.round(timelineProgress) + start;
	function getEntry(year: number) {
		for (let i = 1; i < data.length; i++) {
			const start = data[i - 1].start;
			const end = data[i].start;
			if (year >= start && year < end) {
				return data[i - 1];
			}
		}
		return data[data.length - 1];
	}
	$: entry = getEntry(year);
</script>

<ScrollHijacker
	height="400vh"
	on:progress={(event) => (scrollProgress = Math.min(event.detail, 1 - Number.EPSILON))}
>
	<div class="container">
		<div class="timeline" style:--timeline-progress={timelineProgress}>
			{#each years as timelinePoint}
				<span class:active={year === timelinePoint}>{timelinePoint}</span>
			{/each}
		</div>
		<div class="content">
			{#each entry.content as block}
				<span class:big={typeof block === 'object'}>
					{typeof block === 'object' ? block.em : block}
				</span>
			{/each}
		</div>
	</div>
</ScrollHijacker>

<style>
	.container {
		display: grid;
		gap: 100px;
		grid-template-rows: 1fr 1fr;
	}

	.timeline {
		color: var(--highlight);
		transform: translateX(calc(-25vw * var(--timeline-progress)));
		align-self: end;
		justify-self: start;
		border-top: 2px solid currentColor;
		min-width: 100%;
		display: flex;
		padding: 0 37.5vw;
	}

	.timeline span {
		position: relative;
		display: grid;
		place-items: center;
		width: 25vw;
		margin-top: 40px;
		font-size: 14px;
	}

	.timeline span::before {
		content: '';
		border-radius: 3px;
		border: 3px solid currentColor;
		position: absolute;
		top: -44px;
		left: 48%;
	}

	.timeline span.active {
		font-size: 30px;
		color: var(--foreground);
	}

	.content {
		font-size: 18px;
		display: grid;
		gap: 15px;
		text-align: center;
		padding: 0 20px;
	}

	.big {
		font-size: 28px;
	}

	@media (min-width: 900px) {
		.container {
			gap: 100px;
			grid-template-columns: 3fr 2fr;
			grid-template-rows: 100vh;
			width: 100%;
		}

		.timeline {
			order: 2;
			transform: translateY(calc(-25vh * var(--timeline-progress)));
			flex-direction: column;
			border-left: 2px solid currentColor;
			border-top: none;
			align-self: start;
			min-width: auto;
			padding: 37.5vh 0;
		}

		.timeline span {
			position: relative;
			width: auto;
			height: 25vh;
			margin-top: 0;
			margin-left: 95px;
			font-size: 52px;
		}

		.timeline span::before {
			content: '';
			border-radius: 4px;
			border: 4px solid currentColor;
			position: absolute;
			left: -100px;
			top: 48%;
		}

		.timeline span.active {
			font-size: 160px;
		}

		.content {
			align-self: center;
			font-size: 36px;
		}

		.big {
			font-size: 66px;
		}
	}
</style>
