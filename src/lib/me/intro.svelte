<script lang="ts">
	import Logo from '$lib/logo.svelte';
	import ScrollHijacker from '$lib/scroll-hijacker.svelte';
</script>

<ScrollHijacker height="400vh" threshold={0.25}>
	<a href="/" class="logo">
		<Logo />
	</a>
	<div class="content">
		Hello! I'm Carlos Marchal. A Chief Technology Officer & Software Engineer who's passionate about
		building software.
	</div>
	<div class="marquee">Some cool sounding motivational bullshit</div>
</ScrollHijacker>

<style>
	.logo {
		color: inherit;
		position: absolute;
		top: 50px;
		left: 35px;
	}

	.content {
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
