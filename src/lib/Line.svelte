<script lang="ts">
    import { ParallaxLayer } from "svelte-parallax";

    export let offset: number;
    export let line: string;
</script>

<slot />

<ParallaxLayer {offset}>
    <p class="line">{line}</p>
</ParallaxLayer>

<style>
    p.line {
        @apply absolute top-1/2 w-full -translate-y-1/2 gap-[10vh] px-[15vw] text-3xl font-bold text-left;
    }
</style>