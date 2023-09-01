<script>
    // import BlogHeader from "$lib/Blog/BlogHeader.svelte";
    import BlogFooter from "$lib/Blog/BlogFooter.svelte";
</script>

<div class="bg-slate-950 relative min-h-screen">
    <!-- <BlogHeader/> -->

    <main class="max-w-5xl mx-auto px-2 sm:px-8 py-8">
        <slot />
    </main>

    <BlogFooter/>
</div>
