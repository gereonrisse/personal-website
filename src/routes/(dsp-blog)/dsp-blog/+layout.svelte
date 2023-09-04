<script>
    import Footer from "$lib/Footer.svelte";
</script>

<div class="relative bg-slate-950 min-h-screen">
    <!-- <BlogHeader/> -->

    <main class="max-w-5xl mx-auto px-6 sm:px-8 pt-8 pb-48">
        <slot />
    </main>

    <!-- <BlogFooter/> -->
    <Footer />
</div>
