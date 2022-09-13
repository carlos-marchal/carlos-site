<section>
	<div class="intro">
		<header>haddock</header>
		<div>
			Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec vel risus in ante posuere
			fermentum. Sed ut rhoncus sapien. Suspend.
			<a href="https://en.haddock.app">Go to haddock</a>
		</div>
	</div>
	<ul>
		<li><span>2020</span><span>fundado durante la pandemia en pleno confinamiento.</span></li>
		<li><span>2020</span><span>fundado durante la pandemia en pleno confinamiento.</span></li>
		<li><span>2020</span><span>fundado durante la pandemia en pleno confinamiento.</span></li>
		<li><span>2020</span><span>fundado durante la pandemia en pleno confinamiento.</span></li>
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

	a {
		color: var(--white);
		margin: 20px 0;
		padding: 15px 45px;
		border-radius: 100px;
		border: 1px solid currentColor;
		display: block;
		width: max-content;
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
		border: 1px solid var(--highlight);
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
