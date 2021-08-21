<script>
    import Header from '@/components/SearchHeader.svelte';
    import Footer from '@/components/SearchFooter.svelte';
</script>



<div class="mx-auto flex flex-col h-screen w-full">
    <header class="px-6">
        <Header />
    </header>
    <main class="container mx-auto flex-1 justify-center mt-5 h-screen">
        <slot />
    </main>
    <hr>
    <footer class="bg-cool-gray-200 px-5">
        <Footer />
    </footer>
</div>

