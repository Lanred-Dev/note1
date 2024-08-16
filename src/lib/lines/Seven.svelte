<script lang="ts">
    import Line from "$lib/Line.svelte";
    import { ParallaxLayer } from "svelte-parallax";

    const offset: number = 6;
    let personScale: number = 1;
    let personPosition: number = 100;
    let explosionScale: number = 1;

    function onProgress(progress: number) {
        personScale = 1 / progress - 1;
        personPosition = Math.max(0, 1000 - 1000 * (progress + 0.3));
        explosionScale = personPosition === 0 ? Math.min((progress - (1 - (personPosition / 1000 + 0.3))) / 0.2, 1) : 0;
    }
</script>

<Line {offset} line={"It is time for us to reclaim,"}>
    <ParallaxLayer {offset} rate={0.5} {onProgress}>
        <div class="relative top-[55%] aspect-square w-full overflow-hidden">
            <div style="--tw-scale-x: {personScale}; --tw-scale-y: {personScale};  --tw-translate-x: {-personPosition - 50}%; will-change: transform, filter;" class="absolute left-1/2 top-1/2 aspect-square w-[7%] -translate-y-1/2 rounded-full bg-white" />

            <div style="--tw-scale-x: {personScale}; --tw-scale-y: {personScale}; --tw-translate-x: {personPosition - 50}%; will-change: transform, filter;" class="absolute left-1/2 top-1/2 aspect-square w-[7%] -translate-y-1/2 rounded-full bg-white" />

            <div style="--tw-scale-x: {explosionScale}; --tw-scale-y: {explosionScale}; will-change: transform, filter;" class="absolute left-1/2 top-1/2 aspect-square w-[50%] -translate-x-1/2 -translate-y-1/2 rounded-full bg-green-100 blur-xl" />
        </div>
    </ParallaxLayer>
</Line>
