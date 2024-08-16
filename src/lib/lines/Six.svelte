<script lang="ts">
    import Line from "$lib/Line.svelte";
    import { ParallaxLayer } from "svelte-parallax";

    const offset: number = 5;
</script>

<Line {offset} line={"Never since you came into view;"}>
    <ParallaxLayer {offset} rate={1}>
        <div class="absolute left-1/2 top-3/4 aspect-square w-[50vw] -translate-x-1/2 rotate-45 rounded-[100%_0px] border-2 border-white">
            <div class="eyeball absolute left-1/2 top-1/2 aspect-square w-[30%] -translate-x-1/2 -translate-y-1/2 rounded-full bg-slate-600">
                <div class="pupil absolute left-1/2 top-1/2 aspect-square w-[30%] -translate-x-1/2 -translate-y-1/2 rounded-full bg-gray-950" />
            </div>
        </div>
    </ParallaxLayer>
</Line>

<style lang="postcss">
    .eyeball {
        animation: eyeball 5s ease-in-out infinite;
    }

    @keyframes eyeball {
        0%,
        90%,
        100% {
            transform: translateX(-50%) translateY(-50%);
        }

        30%,
        40% {
            transform: translateX(-30%) translateY(-60%);
        }

        65%,
        75% {
            transform: translateX(-80%) translateY(-45%);
        }
    }

    .pupil {
        animation: pupil 5s ease-in-out infinite;
    }

    @keyframes pupil {
        0%,
        90%,
        100% {
            transform: translateX(-50%) translateY(-50%);
        }

        32%,
        42% {
            transform: translateX(-10%) translateY(-30%);
        }

        67%,
        77% {
            transform: translateX(-80%) translateY(-45%);
        }
    }
</style>
