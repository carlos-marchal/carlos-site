<script>
	import ButtonLink from '$lib/button-link.svelte';
</script>

<section>
	<div class="intro">
		<header>haddock</header>
		<div>
			<p>
				My co-founders and I started haddock 3 years ago at the height of the pandemic. We wanted to
				help restaurants take control of their bookkeeping. For lots of them, staying open or having
				to close came down to optimising to the last cent.
			</p>
			<p>Check out what we do in depth:</p>
			<div class="cta">
				<ButtonLink href="https://en.haddock.app">
					Go to haddock<span slot="hover">https://en.haddock.app</span>
				</ButtonLink>
			</div>
		</div>
	</div>
	<ul>
		<li><span>1000</span><span>paying customers across Southern Europe and LATAM</span></li>
		<li><span>$50k</span><span>of monthly recurring revenue</span></li>
		<li><span>$2M</span><span>in total external funding</span></li>
		<li><span>35+</span><span>employees on the haddock team</span></li>
	</ul>
</section>

<style>
	section {
		padding: 0 46px;
		font-size: 18px;
		line-height: 32px;
	}

	header {
		margin: 0 -50px 30px -50px;
		font-size: 52px;
	}

	.cta {
		margin: 20px 0;
		width: 300px;
		height: 80px;
	}

	ul {
		display: grid;
		margin: 40px 0;
		grid-template-columns: 1fr 1fr;
		gap: 30px;
	}

	li {
		display: grid;
		position: relative;
		padding-top: 20px;
		font-size: 14px;
	}

	li::before {
		content: '';
		position: absolute;
		width: 60%;
		border-top: 2px solid var(--highlight);
	}

	li span:first-child {
		font-size: 32px;
	}

	@media (min-width: 900px) {
		.intro {
			display: grid;
			grid-template-columns: 4fr 2fr 1fr;
			margin: 200px 0;
			place-items: center;
		}

		header {
			font-size: 180px;
			justify-self: start;
		}

		ul {
			max-width: 500px;
			margin-left: 150px;
			gap: 50px;
		}

		li span:first-child {
			font-size: 50px;
			line-height: 60px;
		}
	}
</style>
