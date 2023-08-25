<div class="py-4 rounded-md hover:bg-slate-900/25 flex flex-col sm:flex-row gap-4 sm:gap-12 max-w-sm sm:max-w-full mx-auto sm:mx-0 px-2">

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
                <slot name="header" />
            </h2>

            <h3 class="text-base font-semibold text-slate-400 hover:text-slate-300">
                <slot name="company" />
            </h3>

            <p class="mt-4 text-sm text-slate-300">
                <slot name="description" />
            </p>

            <div class="mt-4">
                <slot name="tags" />
            </div>
        </div>
    </div>

</div>