<script>
	import LogoRound from '$lib/logo-round.svelte';
</script>

<section>
	<div>
		Feel free to contact anytime. Here's an <a href="mailto:carlos.marchal@pm.me">email</a>.
	</div>
	<ul>
		<li><a href="mailto:carlos.marchal@pm.me">carlos.marchal@pm.me</a></li>
		<li><a href="tel:+34618282208">+34 618 28 22 08</a></li>
		<li><a href="https://www.linkedin.com/in/carlosmarchal">Linkedin</a></li>
	</ul>
	<a class="logo" href="/"><LogoRound /></a>
</section>

<style>
	section {
		margin: 90px 45px;
		display: grid;
		gap: 20px;
	}

	div {
		font-size: 30px;
	}

	ul {
		line-height: 40px;
	}

	a {
		color: inherit;
	}

	div a {
		text-decoration: underline;
	}

	a.logo {
		display: block;
		height: 150px;
		width: 150px;
		justify-self: end;
	}

	@media (min-width: 900px) {
		section {
			margin: 90px 150px;
			grid-template-columns: 1fr 1fr;
			grid-template-rows: 1fr 1fr;
		}

		a.logo {
			grid-area: 1 / 2 / 3 / 3;
			align-self: end;
		}

		div {
			font-size: 40px;
			max-width: 600px;
		}
	}
</style>
