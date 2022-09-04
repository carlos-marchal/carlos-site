<script lang="ts">
	import { onMount } from 'svelte';
	import Logo from '$lib/logo.svelte';

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
				<a href="/me"><span>About me</span><span>README.md</span></a>
			</li>
			<li style:animation-delay="1.6s"><a href="/blog"><span>Blog</span><span>blog/</span></a></li>
			<li style:animation-delay="1.7s" style:grid-column="span 1">
				<a href="https://github.com/carlos-marchal">
					<span>GitHub</span><span>.git</span>
				</a>
			</li>
			<li style:animation-delay="1.7s" style:grid-column="span 1">
				<a href="https://linkedin.com/in/carlosmarchal">
					<span>LinkedIn</span><span>linkedin -> https://linkedin.com/in/carlosmarchal</span>
				</a>
			</li>
			<li style:animation-delay="1.8s">
				<a href="https://en.haddock.app">
					<span>haddock</span><span>haddock -> https://en.haddock.app</span>
				</a>
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

	a {
		--foreground: var(--white);
		display: grid;
		position: relative;
		place-items: center;
		height: 100%;
		border: 2px solid var(--foreground);
		border-radius: 50px;
		font-size: 20px;
		overflow: hidden;
	}

	a:hover {
		text-decoration: none;
	}

	a > span:last-child {
		position: absolute;
		--foreground: var(--black);
		--background: var(--white);
		font: 16px 'Noto Sans Mono';
		color: var(--foreground);
		background: var(--background);
		height: 100%;
		width: 100%;
		display: grid;
		place-items: center;
		text-align: center;
		clip-path: inset(0 100% 0 0);
		transition: 500ms clip-path;
	}

	a:hover > span:last-child {
		clip-path: inset(0 0% 0 0);
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
