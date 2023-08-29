<script>
	import { browser } from '$app/environment';
	import { page } from '$app/stores';
	import { webVitals } from '$lib/vitals';
	import "../app.css";
	import Header from "$lib/Header.svelte";
	import Footer from "$lib/Footer.svelte";
	import {locale} from "$lib/translations/index.js";
	import {onMount} from "svelte";

	/** @type {import('./$types').LayoutServerData} */
	export let data;

	// Vercel Analytics.
	$: if (browser && data?.analyticsId) {
		webVitals({
			path: $page.url.pathname,
			params: $page.params,
			analyticsId: data.analyticsId
		});
	}

	onMount(() => {
		// Translations.
		$locale = window.localStorage.locale || getLocaleFromBrowser();
	});

	function getLocaleFromBrowser() {
		const supportedLocales = ['en', 'de'];
		const browserLocale = navigator.language.split('-')[0];

		return supportedLocales.includes(browserLocale) ? browserLocale : 'en';
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
	/*.app {
		background: linear-gradient(180deg, theme('colors.slate.900') 0%, theme('colors.violet.950') 100%);
	}*/
	.app {
		background: radial-gradient(
				circle at 50% 50%,
				theme('colors.violet.950'),
				theme('colors.slate.900')
		);
	}
</style>