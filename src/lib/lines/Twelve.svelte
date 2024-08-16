<script lang="ts">
    import Line from "$lib/Line.svelte";
    import { ParallaxLayer } from "svelte-parallax";

    const offset: number = 11;
    let blur: number = 1;

    function onProgress(progress: number) {
        blur = progress > 0.4 ? 101 - (100 * ((progress - 0.4) / 0.1)) : 100;
    }
</script>

<Line {offset} line={"Meeting every challenge undaunted and graced."}>
    <ParallaxLayer {offset} rate={0.6} {onProgress}>
        <div style="--tw-blur: blur({blur}px); will-change: blur;" class="absolute left-1/2 top-3/4 aspect-square w-[25%] -translate-x-1/2 blur-0">
            <svg class="h-full w-full fill-rose-600" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
                <path d="m11.645 20.91-.007-.003-.022-.012a15.247 15.247 0 0 1-.383-.218 25.18 25.18 0 0 1-4.244-3.17C4.688 15.36 2.25 12.174 2.25 8.25 2.25 5.322 4.714 3 7.688 3A5.5 5.5 0 0 1 12 5.052 5.5 5.5 0 0 1 16.313 3c2.973 0 5.437 2.322 5.437 5.25 0 3.925-2.438 7.111-4.739 9.256a25.175 25.175 0 0 1-4.244 3.17 15.247 15.247 0 0 1-.383.219l-.022.012-.007.004-.003.001a.752.752 0 0 1-.704 0l-.003-.001Z" />
            </svg>
        </div>

        <div class="absolute left-1/2 top-3/4 aspect-square w-[25%] -translate-x-1/2 blur-3xl">
            <svg class="h-full w-full fill-rose-600" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
                <path d="m11.645 20.91-.007-.003-.022-.012a15.247 15.247 0 0 1-.383-.218 25.18 25.18 0 0 1-4.244-3.17C4.688 15.36 2.25 12.174 2.25 8.25 2.25 5.322 4.714 3 7.688 3A5.5 5.5 0 0 1 12 5.052 5.5 5.5 0 0 1 16.313 3c2.973 0 5.437 2.322 5.437 5.25 0 3.925-2.438 7.111-4.739 9.256a25.175 25.175 0 0 1-4.244 3.17 15.247 15.247 0 0 1-.383.219l-.022.012-.007.004-.003.001a.752.752 0 0 1-.704 0l-.003-.001Z" />
            </svg>
        </div>
    </ParallaxLayer>
</Line>

<style lang="postcss">
    svg {
        animation: heartbeat 1s infinite alternate;
    }

    @keyframes heartbeat {
        0% {
            transform: scale(1);
        }

        50% {
            transform: scale(1.1);
        }

        100% {
            transform: scale(1);
        }
    }
</style>
