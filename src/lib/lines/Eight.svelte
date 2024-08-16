<script lang="ts">
    import Line from "$lib/Line.svelte";
    import { ParallaxLayer } from "svelte-parallax";

    const offset: number = 7;
    const startColor: string = "#e11d48";
    const endColor: string = "#22c55e";
    let color: string = "#000000";

    function interpolateColor(color1: string, color2: string, factor: number): string {
        // Convert hex colors to RGB
        const rgb1 = parseInt(color1.slice(1), 16);
        const rgb2 = parseInt(color2.slice(1), 16);

        // Extract RGB components
        const r1 = (rgb1 >> 16) & 0xff;
        const g1 = (rgb1 >> 8) & 0xff;
        const b1 = rgb1 & 0xff;

        const r2 = (rgb2 >> 16) & 0xff;
        const g2 = (rgb2 >> 8) & 0xff;
        const b2 = rgb2 & 0xff;

        // Interpolate RGB components
        const r = Math.round(r1 + factor * (r2 - r1));
        const g = Math.round(g1 + factor * (g2 - g1));
        const b = Math.round(b1 + factor * (b2 - b1));

        // Convert RGB back to hex
        return `#${((1 << 24) + (r << 16) + (g << 8) + b).toString(16).slice(1).toUpperCase()}`;
    }

    function onProgress(progress: number) {
        color = interpolateColor(startColor, endColor, progress > 0.5 ? (progress - 0.5) / 0.2 : 0);
    }
</script>

<Line {offset} line={"Reclaim what we once thought was true."}>
    <ParallaxLayer {offset} rate={0.6} {onProgress}>
        <svg style="fill: {color};" class="absolute left-1/2 top-[70%] aspect-square w-[35%] -translate-x-[130%]" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
            <path fill-rule="evenodd" d="M19.916 4.626a.75.75 0 0 1 .208 1.04l-9 13.5a.75.75 0 0 1-1.154.114l-6-6a.75.75 0 0 1 1.06-1.06l5.353 5.353 8.493-12.74a.75.75 0 0 1 1.04-.207Z" clip-rule="evenodd" />
        </svg>
    </ParallaxLayer>

    <ParallaxLayer {offset} rate={0.8} {onProgress}>
        <svg style="fill: {color};" class="absolute left-1/2 top-[63%] aspect-square w-[39%] translate-x-[30%]" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
            <path fill-rule="evenodd" d="M19.916 4.626a.75.75 0 0 1 .208 1.04l-9 13.5a.75.75 0 0 1-1.154.114l-6-6a.75.75 0 0 1 1.06-1.06l5.353 5.353 8.493-12.74a.75.75 0 0 1 1.04-.207Z" clip-rule="evenodd" />
        </svg>
    </ParallaxLayer>

    <ParallaxLayer {offset} rate={1} {onProgress}>
        <svg style="fill: {color};" class="absolute left-1/2 top-2/3 aspect-square w-[43%] -translate-x-1/2" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
            <path fill-rule="evenodd" d="M19.916 4.626a.75.75 0 0 1 .208 1.04l-9 13.5a.75.75 0 0 1-1.154.114l-6-6a.75.75 0 0 1 1.06-1.06l5.353 5.353 8.493-12.74a.75.75 0 0 1 1.04-.207Z" clip-rule="evenodd" />
        </svg>
    </ParallaxLayer>
</Line>
