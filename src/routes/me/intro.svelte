<script lang="ts">
	import Logo from '$lib/logo.svelte';
	import ScrollHijacker from '$lib/scroll-hijacker.svelte';
</script>

<ScrollHijacker height="400vh" threshold={0}>
	<a href="/" class="logo">
		<Logo />
	</a>
	<div class="content">
		Hello! My name is Carlos Marchal. I'm a software engineer who's passionate about building great
		software. I'm currently working as co-founder and CTO at haddock, but I'm already looking for my
		next adventure!

		<div class="scroll-down">
			<div>scroll down</div>
			<svg
				width="17"
				height="28"
				viewBox="0 0 17 28"
				fill="none"
				xmlns="http://www.w3.org/2000/svg"
				stroke-width="2"
				stroke-linecap="round"
				stroke-linejoin="round"
				stroke="currentColor"
			>
				<path d="M8.66699 26.6667L8.66699 1.00002" />
				<path d="M1.33366 19.3334L8.66699 26.6667" />
				<path d="M16 19.3334L8.66667 26.6667" />
			</svg>
		</div>
	</div>
	<div class="marquee">Let's take 2 minutes to get to know me</div>
</ScrollHijacker>

<style>
	.logo {
		color: inherit;
		position: absolute;
		top: 50px;
		left: 35px;
	}

	.content {
		position: relative;
		margin: 0 38px;
		font-size: 22px;
		text-align: center;
	}

	.marquee {
		position: absolute;
		bottom: 0;
		left: 0;
		line-height: 0.6;
		text-transform: uppercase;
		white-space: nowrap;
		font-size: 52px;
		transform: translateX(calc((100vw - 100%) * var(--progress)));
	}

	@keyframes bounce {
		from {
			transform: translateX(-50%) translateY(70px);
		}

		to {
			transform: translateX(-50%) translateY(90px);
		}
	}

	.scroll-down {
		position: absolute;
		font-size: 18px;
		color: var(--highlight);
		bottom: -20px;
		left: 50%;
		transform: translateX(-50%) translateY(70px);
		animation: 2s ease-in-out alternate infinite bounce;
		opacity: max(1 - var(--progress) * 3, 0);
		pointer-events: none;
	}

	@media (min-width: 900px) {
		.logo {
			top: 100px;
			left: 100px;
		}

		.content {
			margin: 0 auto;
			max-width: 1000px;
			font-size: 35px;
		}

		.marquee {
			font-size: 150px;
		}
	}
</style>
