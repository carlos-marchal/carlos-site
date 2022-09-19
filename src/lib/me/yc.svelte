<script lang="ts">
	import yc from './yc-logo.svg';
	const REVOLUTION_HEIGHT = 3000;
	let scrollY: number;
	$: revolution = (scrollY % REVOLUTION_HEIGHT) / REVOLUTION_HEIGHT;
</script>

<section>
	<svg
		width="168"
		height="168"
		viewBox="0 0 168 166"
		fill="none"
		xmlns="http://www.w3.org/2000/svg"
		style:transform={`translateX(50%) rotate(${revolution}turn)`}
	>
		<path
			d="M0 56.5909L17.7882 26.4091L71.1529 62.25L65.2235 0H102.776L96.8471 62.25L150.212 26.4091L168 56.5909L108.706 83L168 109.409L150.212 139.591L96.8471 103.75L102.776 166H65.2235L71.1529 103.75L17.7882 139.591L0 109.409L59.2941 83L0 56.5909Z"
			fill="white"
		/>
	</svg>

	<img src={yc} alt="Y Combinator logo" height="100" width="100" />
	<div>
		<div class="subtitle">2022</div>
		<div class="title">Y Combinator</div>
		<div>
			Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec vel risus in ante posuere
			fermentum. Sed ut rhoncus sapien. Suspendisse potenti. Proin eget finibus nibh. Integer justo
			magna, vehicula nec orci in, congue porta augue. Sed augue urna, ultrices id dignissim.
		</div>
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
		transform: translateX(50%);
	}

	img {
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
</style>
