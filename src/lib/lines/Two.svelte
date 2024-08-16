<script lang="ts">
    import Line from "$lib/Line.svelte";
    import { ParallaxLayer } from "svelte-parallax";

    const offset: number = 1;
</script>

<Line {offset} line={"Your voice, a shining light;"}>
    <ParallaxLayer {offset} rate={1}>
        <div class="w-[50vw] aspect-square blur-3xl bg-yellow-400 rounded-full absolute top-3/4 left-1/2 -translate-x-1/2" />
    </ParallaxLayer>
</Line>

<style lang="postcss">
    div {
        animation: shine 5s ease-in-out infinite;
    }

    @keyframes shine {
        0%, 50%, 100% {
            opacity: 0.5;
        }

        30%, 80% {
            opacity: 0.7;
        }
    }
</style>