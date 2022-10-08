<script lang="ts">
	const skills = [
		{
			progress: 0.95,
			title: 'Coding',
			content:
				"As many developers do, I started coding as a young teen. I've worked with all kinds of languages and paradigms: static types, dinamic types, compiled, interpreted, object oriented, functional... What's important is choosing the right tool for the job, and writing clean and idiomatic code."
		},
		{
			progress: 0.9,
			title: 'Fullstack',
			content:
				'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin vel varius ipsum. Mauris eros metus,'
		},
		{
			progress: 0.8,
			title: 'Systems design',
			content:
				'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin vel varius ipsum. Mauris eros metus,'
		},
		{
			progress: 0.7,
			title: 'Behaviour driven',
			content:
				'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin vel varius ipsum. Mauris eros metus,'
		},
		{
			progress: 0.8,
			title: 'Team worker',
			content:
				'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin vel varius ipsum. Mauris eros metus,'
		},
		{
			progress: 0.7,
			title: 'Product centered',
			content:
				'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin vel varius ipsum. Mauris eros metus,'
		}
	];
</script>

<section>
	<header>My Skills</header>
	<ul>
		{#each skills as { progress, title, content }}
			<li>
				<svg>
					<rect y="66%" width="100%" height="33%" fill="var(--foreground)" />
					<rect y="0%" width="{progress * 100}%" height="100%" fill="var(--highlight)" />
				</svg>
				<div class="title">{title}</div>
				<div>{content}</div>
			</li>
		{/each}
	</ul>
</section>

<style>
	section {
		margin: 45px;
	}

	header {
		font-size: 25px;
		margin: 15px 0;
	}

	header::after {
		content: ' []';
	}

	ul {
		display: grid;
		gap: 50px;
	}

	svg {
		width: 80%;
		height: 6px;
	}

	.title {
		font-size: 22px;
		margin: 15px 0;
	}

	@media (min-width: 900px) {
		section {
			margin: 45px 150px;
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
