<script>
    import NewTab from "$lib/svg/NewTab.svelte";

    export let href = '#';
</script>

<a href="{href}" target="_blank" class="flex flex-row gap-2">
    <slot />
    <div class="w-4 h-4 mt-1">
        <NewTab />
    </div>
</a>
