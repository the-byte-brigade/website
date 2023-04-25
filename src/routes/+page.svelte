<script>
    import Header from "../components/Header.svelte";
    import Quote from "../components/Quote.svelte";
    import About from "../components/About.svelte";
    import Carousel from "../components/Carousel.svelte";
    import Footer from "../components/Footer.svelte";
</script>

<body class="flex flex-col bg-lime-300">
    <br><br><br>
    <div class="flex justify-center align-center gap-4">
        <Quote />
        <Carousel />
    </div>

    <About/>
</body>
