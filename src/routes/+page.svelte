<script lang="ts">
    import One from "$lib/lines/One.svelte";
    import Two from "$lib/lines/Two.svelte";
    import Three from "$lib/lines/Three.svelte";
    import Four from "$lib/lines/Four.svelte";
    import Five from "$lib/lines/Five.svelte";
    import Six from "$lib/lines/Six.svelte";
    import Seven from "$lib/lines/Seven.svelte";
    import Eight from "$lib/lines/Eight.svelte";
    import Nine from "$lib/lines/Nine.svelte";
    import Ten from "$lib/lines/Ten.svelte";
    import Eleven from "$lib/lines/Eleven.svelte";
    import Twelve from "$lib/lines/Twelve.svelte";
    import { Parallax } from "svelte-parallax";
    import { onMount } from "svelte";

    let parallax: Parallax;
    let sectionHeight: Promise<number>;

    onMount(() => {
        sectionHeight = new Promise((resolve) => {
            const height = window.innerHeight;
            resolve(height);
        });
    });
</script>

{#await sectionHeight then height}
    <Parallax sections={12} sectionHeight={height} bind:this={parallax}>
        <One />
        <Two />
        <Three />
        <Four />
        <Five />
        <Six />
        <Seven />
        <Eight />
        <Nine />
        <Ten />
        <Eleven />
        <Twelve />
    </Parallax>
{/await}
