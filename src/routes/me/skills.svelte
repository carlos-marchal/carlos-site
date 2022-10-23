<script lang="ts">
	const skills = [
		{
			progress: 0.95,
			title: 'Coding',
			content:
				"I've worked with all kinds of languages and paradigms: static types, dynamic types, compiled, interpreted, object oriented, functional... What's important is choosing the right tool for the job, and writing clean and idiomatic code."
		},
		{
			progress: 0.9,
			title: 'Fullstack',
			content:
				"From writing CSS stylesheets to setting up VMs on cloud infrastructure, there are no parts of the tech stack I don't enjoy working with."
		},
		{
			progress: 0.87,
			title: 'Systems design',
			content:
				'Having designed and successfully launched haddock, I have confidence in my ability to turn an idea into technical specifications.'
		},
		{
			progress: 0.8,
			title: 'Test driven',
			content:
				"It is for good reason that all new languages ship with integrated testing solutions. You can't rely on behaviours you don't test for."
		},
		{
			progress: 0.85,
			title: 'Team work',
			content:
				"While growing the product team at haddock from just me to 6 people, I discovered both my love for mentoring others and for learning from others' experience."
		},
		{
			progress: 0.8,
			title: 'Product centered',
			content:
				'Features and changes need to have goals that can be tracked and measured. From OKRs to design decisions, a good developer always has the whole picture in mind.'
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
