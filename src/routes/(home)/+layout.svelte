<script>
	import {browser} from '$app/environment';
	import {page} from '$app/stores';
	import {webVitals} from '$lib/vitals';
	import "../../app.css";
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

    // Translations.
    onMount(() => {

        $locale = window.localStorage.locale || getLocaleFromBrowser();
    });

    function getLocaleFromBrowser() {
        const supportedLocales = ['en', 'de'];
        const browserLocale = navigator.language.split('-')[0];

        return supportedLocales.includes(browserLocale) ? browserLocale : 'en';
    }

    // Mouse-responsive background.
    let bgLeft = "50%";
    let bgTop = "50%";

    function handlePointerMove(e) {
        if (!browser) return;

        const {clientX, clientY} = e;
        const {innerWidth, innerHeight} = window;

        bgLeft = Math.round((clientX / innerWidth) * 100) + "%";
        bgTop = Math.round((clientY / innerHeight) * 100) + "%";
    }
</script>

<div class="relative min-h-screen text-white" on:pointermove|preventDefault={handlePointerMove}>
    <Header/>

    <main class="h-full max-w-5xl mx-auto pb-48">
        <slot/>
    </main>

    <Footer/>

    <div class="background fixed inset-0 z-[-1]" style="--bgLeft:{bgLeft}; --bgTop:{bgTop}">

    </div>
</div>

<style>
    .background {
        background: radial-gradient(
                circle at var(--bgLeft) var(--bgTop),
                theme('colors.slate.900'),
                theme('colors.slate.950')
        );
    }
</style>