<script lang="ts">
	import yc from './yc-logo.svg';
	const REVOLUTION_HEIGHT = 3000;
	let scrollY: number;
	$: revolution = (scrollY % REVOLUTION_HEIGHT) / REVOLUTION_HEIGHT;
	const gallery = import.meta.glob<{ default: string }>('./haddock-screenshots/*', { eager: true });
	const sources = Object.values(gallery).map((value) => value.default);
</script>

<section>
	<svg
		width="168"
		height="168"
		viewBox="0 0 168 166"
		fill="none"
		xmlns="http://www.w3.org/2000/svg"
		style:--turns={`${revolution}turn`}
	>
		<path
			d="M0 56.5909L17.7882 26.4091L71.1529 62.25L65.2235 0H102.776L96.8471 62.25L150.212 26.4091L168 56.5909L108.706 83L168 109.409L150.212 139.591L96.8471 103.75L102.776 166H65.2235L71.1529 103.75L17.7882 139.591L0 109.409L59.2941 83L0 56.5909Z"
			fill="white"
		/>
	</svg>

	<div class="main">
		<img src={yc} alt="Y Combinator logo" height="100" width="100" />
		<div class="subtitle">2022</div>
		<div class="title">Y Combinator</div>
		<div class="content">
			Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec vel risus in ante posuere
			fermentum. Sed ut rhoncus sapien. Suspendisse potenti. Proin eget finibus nibh. Integer justo
			magna, vehicula nec orci in, congue porta augue. Sed augue urna, ultrices id dignissim.
		</div>
	</div>
	<div class="gallery">
		{#each sources as src}
			<img {src} alt="Screenshot from haddock app" />
		{/each}
	</div>
</section>
<svelte:window bind:scrollY />

<style>
	section {
		position: relative;
		padding: 0 45px;
		overflow-x: hidden;
	}

	svg {
		position: absolute;
		right: 0;
		top: 0;
		transform: translateX(50%) rotate(var(--turns));
	}

	.main img {
		margin: 30px 0;
	}

	.subtitle {
		font-size: 20px;
	}

	.title {
		font-size: 30px;
		text-transform: uppercase;
		margin-bottom: 20px;
	}

	.gallery {
		display: flex;
		justify-content: space-between;
		height: 300px;
		overflow-x: scroll;
		margin: 45px -45px;
		padding: 0 45px;
		-ms-overflow-style: none;
		scrollbar-width: none;
	}

	.gallery::-webkit-scrollbar {
		display: none;
	}

	.gallery img {
		border-radius: 16px;
	}

	.gallery img:not(:last-child) {
		margin-right: 45px;
	}

	@media (min-width: 900px) {
		.gallery {
			display: grid;
			grid-auto-flow: column;
			gap: 45px;
			height: auto;
		}

		.gallery img {
			width: 100%;
		}

		.gallery img:not(:last-child) {
			margin-right: 0;
		}
	}

	@media (min-width: 1400px) {
		.main {
			display: grid;
			gap: 20px;
			grid:
				' subtitle title title logo' auto
				' . . content .' auto
				/ auto auto 550px 250px;
			justify-content: end;
			align-items: center;
			margin: 0 -45px;
		}

		.main img {
			height: 150px;
			width: 150px;
			margin: 0;
			grid-area: logo;
			justify-self: end;
		}

		.subtitle {
			font-size: 42px;
			grid-area: subtitle;
		}

		.title {
			font-size: 100px;
			grid-area: title;
		}

		.content {
			grid-area: content;
		}

		.gallery {
			margin: 90px -45px;
		}

		svg {
			left: 0;
			transform: translateX(-50%) rotate(var(--turns));
			height: 280px;
			width: 280px;
		}
	}
</style>
