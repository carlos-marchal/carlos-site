<script lang="ts">
	import Intro from './intro.svelte';
	import Timeline from './timeline.svelte';
	import Haddock from './haddock.svelte';
	import YC from './yc.svelte';
	import Skills from './skills.svelte';
	import Footer from './footer.svelte';
	import Languages from './languages.svelte';
</script>

<svelte:head>
	<title>Carlos Marchal</title>
	<meta
		name="description"
		content="Hi! I'm Carlos Marchal, a software engineer, and this is my personal site. Take 2 minutes to get to know me!"
	/>
</svelte:head>

<Intro />
<Timeline />
<Haddock />
<YC />
<Skills />
<Languages />
<Footer />
