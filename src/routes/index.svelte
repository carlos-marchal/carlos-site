<script lang="ts">
	import { onMount } from 'svelte';
	import Logo from '$lib/logo.svelte';
	import ButtonLink from '$lib/button-link.svelte';

	const command = 'ls -ah';
	let prompt = '';

	onMount(() => {
		const interval = setInterval(() => {
			if (command.length !== prompt.length) {
				prompt = prompt + command[prompt.length];
			} else {
				clearInterval(interval);
			}
		}, 200);
		return () => clearInterval(interval);
	});
</script>

<svelte:head>
	<title>Carlos Marchal</title>
</svelte:head>

<main>
	<Logo />
	<div class="intro">
		Hi! I'm Carlos Marchal, a CTO and software engineer who's passionate about building great
		software.
	</div>
	<pre>visitor@mysite:~$ {prompt}<noscript>{command}</noscript></pre>
	<nav>
		<ul>
			<li style:animation-delay="1.5s">
				<ButtonLink href="/me"><span>About me</span><span slot="hover">README.md</span></ButtonLink>
			</li>
			<li style:animation-delay="1.6s">
				<ButtonLink href="/blog"><span>Blog</span><span slot="hover">blog/</span></ButtonLink>
			</li>
			<li style:animation-delay="1.7s" style:grid-column="span 1">
				<ButtonLink href="https://github.com/carlos-marchal">
					<span>GitHub</span><span slot="hover">.git</span>
				</ButtonLink>
			</li>
			<li style:animation-delay="1.7s" style:grid-column="span 1">
				<ButtonLink href="https://linkedin.com/in/carlosmarchal">
					<span>LinkedIn</span><span slot="hover">https://linkedin.com/in/carlosmarchal</span>
				</ButtonLink>
			</li>
			<li style:animation-delay="1.8s">
				<ButtonLink href="https://en.haddock.app">
					<span>haddock</span><span slot="hover">https://en.haddock.app</span>
				</ButtonLink>
			</li>
		</ul>
	</nav>
</main>

<style>
	main {
		box-sizing: border-box;
		padding: 50px 35px;
		min-height: 100vh;
		display: flex;
		flex-direction: column;
		align-items: start;
	}

	.intro {
		margin: 40px 0;
		font-size: 22px;
		max-width: 900px;
		flex-grow: 1;
	}

	nav {
		width: 100%;
	}

	ul {
		display: grid;
		grid-auto-rows: 100px;
		grid-template-columns: 1fr 1fr;
		gap: 15px;
		margin: 30px 0;
	}

	@keyframes appear {
		from {
			opacity: 0;
			transform: translateX(-50px);
		}

		to {
			opacity: 1;
			transform: translateX(0);
		}
	}

	li {
		grid-column: span 2;
		animation: appear 250ms linear backwards;
	}

	@media (min-width: 900px) {
		main {
			padding: 100px;
		}

		ul {
			grid-template-columns: repeat(4, 1fr);
			grid-template-rows: repeat(2, 100px);
		}
	}
</style>
