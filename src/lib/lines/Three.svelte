<script lang="ts">
    import Line from "$lib/Line.svelte";
    import { ParallaxLayer } from "svelte-parallax";

    const offset: number = 2;
    let opacity: number = 0;
    let scale: number = 0.5;

    function onProgress(progress: number) {
        opacity = Math.min(1, progress * 2);
        scale = 1 * (progress + 0.5);
    }
</script>

<Line {offset} line={"They brighten my whole world in a magical way,"}>
    <ParallaxLayer {offset} rate={0.5} {onProgress}>
        <div class="absolute left-1/2 top-1/2 aspect-square w-full -translate-x-1/2 -translate-y-1/2 opacity-70">
            <div class="absolute left-[15%] top-[40%] flex aspect-square w-full items-center justify-center">
                <div style="opacity: {opacity}; scale: {scale};" class="h-full w-full rounded-full bg-red-500 blur-3xl" />
            </div>

            <div class="absolute right-[25%] top-[45%] flex aspect-square w-full items-center justify-center">
                <div style="opacity: {opacity}; scale: {scale};" class="h-full w-full rounded-full bg-violet-500 blur-3xl" />
            </div>

            <div class="absolute bottom-[38%] left-[22%] flex aspect-square w-full items-center justify-center">
                <div style="opacity: {opacity}; scale: {scale};" class="h-full w-full rounded-full bg-rose-400 blur-3xl" />
            </div>

            <div class="absolute left-1/2 top-1/2 flex aspect-square w-full -translate-x-1/2 -translate-y-1/2 scale-90 items-center justify-center">
                <div style="opacity: {opacity}; scale: {scale};" class="h-full w-full rounded-full bg-blue-700 blur-3xl" />
            </div>

            <div class="absolute bottom-[40%] right-[25%] flex aspect-square w-full items-center justify-center">
                <div style="opacity: {opacity}; scale: {scale};" class="h-full w-full rounded-full bg-emerald-500 blur-3xl" />
            </div>
        </div>
    </ParallaxLayer>
</Line>
