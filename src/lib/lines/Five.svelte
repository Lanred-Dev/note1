<script lang="ts">
    import Line from "$lib/Line.svelte";
    import Stars from "$lib/Stars.svelte";
    import { ParallaxLayer } from "svelte-parallax";

    const offset: number = 4;
</script>

<Line {offset} line={"November skies are never the same,"}>
    <ParallaxLayer {offset} rate={0.6}>
        <Stars count={15} starRadius={2.65} />
    </ParallaxLayer>

    <ParallaxLayer {offset} rate={0.3}>
        <Stars count={15} starRadius={2} />
    </ParallaxLayer>
    
    <ParallaxLayer {offset} rate={0.1}>
        <Stars count={15} starRadius={1} />
    </ParallaxLayer>
</Line>