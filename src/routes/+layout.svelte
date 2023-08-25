<script>
	import { browser } from '$app/environment';
	import { page } from '$app/stores';
	import { webVitals } from '$lib/vitals';
	import "../app.css";

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

<div class="app h-screen text-white">
	<main class="h-full px-4 py-8 max-w-5xl mx-auto flex flex-col">
		<slot />
	</main>

	<footer>

	</footer>
</div>

<style>
	.app {
	/* gradient from very dark violet to less dark violet	*/
		background: linear-gradient(180deg, theme('colors.slate.900') 0%, theme('colors.violet.950') 100%);
	}
</style>