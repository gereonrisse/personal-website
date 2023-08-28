<script>
    export let name = "#";
</script>

<a class="my-4 flex flex-col sm:flex-row gap-4 sm:gap-12" id="{name}">
    <div class="hidden sm:inline-block border-t-2 mt-4 w-full border-slate-500"></div>
    <h2 class="px-6 sm:px-0 text-3xl font-bold text-slate-400 whitespace-nowrap text-center">
        <slot />
    </h2>
    <div class="hidden sm:inline-block border-t-2 mt-4 w-full border-slate-500"></div>
</a>