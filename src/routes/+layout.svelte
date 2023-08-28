<script>
	import { browser } from '$app/environment';
	import { page } from '$app/stores';
	import { webVitals } from '$lib/vitals';
	import "../app.css";
	import Header from "$lib/Header.svelte";
	import Footer from "$lib/Footer.svelte";

	/** @type {import('./$types').LayoutServerData} */
	export let data;

	$: if (browser && data?.analyticsId) {
		webVitals({
			path: $page.url.pathname,
			params: $page.params,
			analyticsId: data.analyticsId
		});
	}
</script>

<div class="app min-h-screen text-white">
	<Header />

	<main class="h-full max-w-5xl mx-auto">
		<slot />
	</main>

	<Footer />
</div>

<style>
	.app {
	/* gradient from very dark violet to less dark violet	*/
		background: linear-gradient(180deg, theme('colors.slate.900') 0%, theme('colors.violet.950') 100%);
	}
</style>