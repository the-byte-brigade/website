<script>
    import Header from "../components/Header.svelte";
    import Footer from "../components/Footer.svelte";
</script>


<div class="bg-gradient-to-b from-teal-200 to-lime-200">
    <Header />
    <main class="flex flex-col w-full min-w-full min-h-full max-h-full">
        <slot/>
        
    </main>
    <div id="footer"><Footer /></div>
     
</div>
