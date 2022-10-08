<script lang="ts">
	const languages = [
		{ english: 'English', level: 'C2' },
		{ english: 'French', localized: 'Français', level: 'C1' },
		{ english: 'Spanish', localized: 'Castellano', level: 'Native' },
		{ english: 'Catalan', localized: 'Català', level: 'Native' },
		{ english: 'Chinese', localized: '中文', level: 'Beginner' }
	];
</script>

<section>
	<header>Languages</header>
	<ul>
		{#each languages as { english, localized, level }}
			<li>
				<div class="title">
					{english}{#if localized !== undefined}
						{' / ' + localized}
					{/if}
				</div>
				<div class="subtitle">{level}</div>
			</li>
		{/each}
	</ul>
</section>

<style>
	section {
		margin: 45px;
	}

	header {
		font-size: 22px;
		margin: 15px 0;
	}

	header::after {
		content: ' []';
	}

	ul {
		display: grid;
		gap: 40px;
	}

	.title {
		font-size: 18px;
		margin: 15px 0;
	}

	.subtitle {
		color: var(--highlight);
	}

	@media (min-width: 900px) {
		section {
			margin: 150px;
		}

		header {
			text-align: center;
			margin: 50px 0;
		}

		ul {
			grid-template-columns: 1fr 1fr 1fr;
			gap: 80px;
		}
	}
</style>
