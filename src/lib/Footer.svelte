<script>
    import {t} from "$lib/translations/index.js";

    function showImprint() {
        document.getElementById('imprint').showModal();
    }
</script>

<footer class="absolute bottom-0 mt-32 w-full mx-auto pb-8 flex flex-col text-xs">
    <a class="text-slate-400 hover:text-rose-200 mx-auto font-semibold"
       href="https://github.com/gereonrisse/personal-website"
       target="_blank">
        {$t('common.footer.credit')}
    </a>

    <div class="mt-1 text-slate-400 mx-auto">
        {$t('common.footer.tech-stack')}
    </div>

    <div class="mt-4 flex gap-4 mx-auto">
        <!-- TODO add imprint -->
        <!-- <button class="text-slate-400 hover:text-rose-200" on:click={showImprint}>
            {$t('common.footer.imprint')}
        </button> -->

        <button class="text-slate-400 hover:text-rose-200">
            <a href="/">Home</a>
        </button>

        <!-- vertical divider -->
        <div class="w-px h-5 bg-slate-500"></div>

        <button class="text-slate-400 hover:text-rose-200">
            <a href="/dsp-blog">DSP Blog</a>
        </button>

        <!-- vertical divider -->
        <div class="w-px h-5 bg-slate-500"></div>

        <button class="text-slate-400 hover:text-rose-200">
            <a href="mailto:gereon.risse@gmail.com">{$t('common.footer.contact')}</a>
        </button>
    </div>
</footer>

<dialog id="imprint">
    TODO
</dialog>