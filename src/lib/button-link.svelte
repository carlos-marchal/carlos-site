<script lang="ts">
	export let href: string;
	export let disabled = false;
</script>

<a class:disabled href={disabled ? undefined : href}>
	<span><slot /></span><span><slot name="hover" /></span>
</a>

<style>
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

	a.disabled {
		cursor: not-allowed;
		opacity: 0.6;
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

	a.disabled:hover > span:last-child {
		clip-path: inset(0 100% 0 0);
	}

	@media (min-width: 900px) {
		a:hover > span:last-child {
			clip-path: inset(0 0% 0 0);
		}
	}
</style>
