<script>
    import {locale} from '$lib/translations';
    import GitHub from "$lib/svg/GitHub.svelte";
    import Envelope from "$lib/svg/Envelope.svelte";

    function toggleLocale() {
        const newLocale = locale.get() === 'en' ? 'de' : 'en';

        $locale = newLocale; // Update immediately
        window.localStorage.locale = newLocale; // Store in local storage
    }
</script>

<header class="relative sm:absolute mb-4 sm:mb-0 w-full animate-fade-in-delayed motion-reduce:animate-none">
    <div class="w-full px-4 pt-4 max-w-5xl mx-auto flex justify-end gap-4">
        <!-- mailto -->
        <a class="text-slate-400 hover:text-rose-200 h-5 w-5" href="mailto:gereon.risse@gmail.com">
            <Envelope/>
        </a>

        <!-- GitHub link -->
        <a class="text-slate-400 hover:text-rose-200 h-5 w-5" href="https://github.com/gereonrisse" target="_blank">
            <GitHub/>
        </a>

        <!-- vertical divider -->
        <div class="w-px h-5 bg-slate-500"></div>

        <!-- DSP blog -->
        <a class="mt-0.5 text-xs text-slate-400 hover:text-rose-200" href="/dsp-blog">DSP blog</a>

        <!-- vertical divider -->
        <div class="w-px h-5 bg-slate-500"></div>

        <!-- language toggle -->
        <button class="text-xs text-slate-400 hover:text-rose-200"
                on:click={toggleLocale}>
            {$locale === 'en' ? 'DE' : 'EN'}
        </button>
    </div>
</header>