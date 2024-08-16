<script lang="ts">
    import Line from "$lib/Line.svelte";
    import { ParallaxLayer } from "svelte-parallax";

    const offset: number = 3;
</script>

<Line offset={3} line={"Your words, guiding me through the night."}>
    <ParallaxLayer {offset} rate={0.9}>
        <img class="w-[80vw] absolute left-1/2 -translate-x-1/2 top-1/2 -translate-y-1/2" src="images/guided.png" alt="Guided">
    </ParallaxLayer>
</Line>
