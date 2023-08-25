<script>
    import { locale } from '$lib/translations';

    function toggleLocale() {
        locale.set(locale.get() === 'en' ? 'de' : 'en');
    }
</script>

<header class="px-4 pt-4 max-w-5xl mx-auto flex justify-end">
    <button class="text-xs text-slate-400 hover:text-slate-200"
            on:click={toggleLocale}>
        {$locale === 'en' ? 'DE' : 'EN'}
    </button>
</header>