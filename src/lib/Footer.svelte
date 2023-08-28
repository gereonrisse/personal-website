<script>
    function showImprint() {
        document.getElementById('imprint').showModal();
    }
</script>

<footer class="mt-32 w-full mx-auto pb-8 max-w-5xl flex flex-col">
    <a class="text-sm text-slate-400 hover:text-slate-200 mx-auto font-semibold"
       target="_blank"
       href="https://github.com/gereonrisse/personal-website">
        Designed and built by Gereon Risse
    </a>

    <div class="mt-1 text-sm text-slate-400 hover:text-slate-200 mx-auto">
        Built with SvelteKit and Tailwind CSS, deployed on Vercel
    </div>

    <div class="mt-4 flex gap-4 mx-auto">
        <button class="text-sm text-slate-400 hover:text-slate-200" on:click={showImprint}>Imprint</button>

        <!-- vertical divider -->
        <div class="w-px h-5 bg-slate-500"></div>

        <a class="text-sm text-slate-400 hover:text-slate-200"
           href="mailto:gereon.risse@gmail.com">
            Contact
        </a>
    </div>
</footer>

<dialog id="imprint">
    TODO
</dialog>