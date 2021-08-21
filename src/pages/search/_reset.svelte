<script>
    import Header from '@/components/ResultHeader.svelte';
    import Footer from '@/components/ResultFooter.svelte';
</script>




<div class="mx-auto flex flex-col h-screen w-full">
    <header class="px-10 shadow">
        <Header />
    </header>
    <main class="container mx-auto flex-1 justify-center mt-5 h-screen">
        <slot />
    </main>
</div>