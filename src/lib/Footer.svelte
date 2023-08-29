<script>
    import {t} from "$lib/translations/index.js";

    function showImprint() {
        document.getElementById('imprint').showModal();
    }
</script>

<footer class="mt-32 w-full mx-auto pb-8 max-w-5xl flex flex-col">
    <a class="text-sm text-slate-400 hover:text-rose-200 mx-auto font-semibold"
       target="_blank"
       href="https://github.com/gereonrisse/personal-website">
        {$t('common.footer.credit')}
    </a>

    <div class="mt-1 text-sm text-slate-400 mx-auto">
        {$t('common.footer.tech-stack')}
    </div>

    <div class="mt-4 flex gap-4 mx-auto">
        <button class="text-sm text-slate-400 hover:text-rose-200" on:click={showImprint}>
            {$t('common.footer.imprint')}
        </button>

        <!-- vertical divider -->
        <div class="w-px h-5 bg-slate-500"></div>

        <a class="text-sm text-slate-400 hover:text-rose-200"
           href="mailto:gereon.risse@gmail.com">
            {$t('common.footer.contact')}
        </a>
    </div>
</footer>

<dialog id="imprint">
    TODO
</dialog>