<div class="px-4 sm:px-2 py-4 rounded-md hover:bg-slate-800/50 flex flex-col sm:flex-row gap-4 sm:gap-12 max-w-sm sm:max-w-full w-full mx-auto sm:mx-0">

    <!-- left side (timespan) -->
    <div class="sm:pl-12 sm:basis-1/3 mt-1 text-sm font-semibold tracking-wide text-slate-400">
        <div class="sm:float-right">
            <slot name="timespan"/>
        </div>
    </div>

    <!-- right side -->
    <div class="sm:pr-12 sm:basis-2/3">
        <div class="max-w-sm">
            <h2 class="text-lg font-bold text-slate-100">
                <slot name="header"/>
            </h2>

            <h3 class="text-base font-semibold text-slate-400 hover:text-rose-300">
                <slot name="company"/>
            </h3>

            <p class="mt-4 text-sm text-slate-300 leading-relaxed">
                <slot name="description"/>
            </p>

            {#if $$slots.tags}
                <div class="mt-4">
                    <slot name="tags"/>
                </div>
            {/if}
        </div>
    </div>

</div>