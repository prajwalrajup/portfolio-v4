
<script>
    import { onMount } from "svelte";
    import ContactMe from "../components/ContactMe.svelte";
    import Header from "../components/Header.svelte";
    import SplashScreen from "../components/SplashScreen.svelte";
    import "./styles.css";
    import "animate.css";
    import AOS from "aos";
    import "aos/dist/aos.css";
    export let data;

    let showSplash = true;

    onMount(() => {
        setTimeout(() => {
            showSplash = false;
        }, 800);
        setTimeout(() => {
            AOS.init({
                once: true,
                duration: 900,
                easing: "ease-in-out",
            });
        }, 0);
    });
</script>

{#if showSplash}
    <SplashScreen />
{:else}
    <div class="app flex flex-col p-3 lg:p-10">
        <Header />

        <main>
            <slot />
        </main>

        <footer>
            <ContactMe contactDetails={data.data.contactDetails} />
        </footer>
    </div>
{/if}
