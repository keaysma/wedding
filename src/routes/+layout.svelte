<script lang="ts">
	import favicon from '$lib/assets/favicon.ico';
	import '../app.scss';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<title>{"Raquel ♥ Michael"}</title>
	<style>
	@import url('https://fonts.googleapis.com/css2?family=Fleur+De+Leah&display=swap');

	.fleur-de-leah-regular {
		font-family: "Fleur De Leah", cursive;
		font-weight: 400;
		font-style: normal;
	}

	@font-face {
		font-family: 'Digital-7';
		src: url('/fonts/digital-7.ttf') format('truetype');
	}

	@font-face {
		font-family: '7Segment';
		src: url('/fonts/7segment.woff') format('woff');
	}
	</style>
</svelte:head>

{@render children()}
