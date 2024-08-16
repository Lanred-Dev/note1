<script lang="ts">
    import { onMount } from "svelte";

    export let count: number = 15;
    export let starRadius: number = 1;
    let canvas: HTMLCanvasElement;
    let context: CanvasRenderingContext2D;
    const stars: { x: number; y: number; opacity: number; increment: number; factor: number }[] = [];
    const padding: number = 20;

    function animate() {
        context.clearRect(0, 0, canvas.width, canvas.height);

        stars.forEach((star) => {
            context.save();
            context.translate(star.x, star.y);

            if (star.opacity > 1) {
                star.factor = -1;
            } else if (star.opacity <= 0) {
                star.factor = 1;
                star.x = Math.round(Math.random() * (canvas.width - 2 * padding)) + padding;
                star.y = Math.round(Math.random() * (canvas.height - 2 * padding)) + padding;
            }

            star.opacity += star.increment * star.factor;

            context.beginPath();
            context.arc(0, 0, starRadius, 0, 2 * Math.PI);
            context.closePath();
            context.fillStyle = `rgba(255, 255, 200, ${star.opacity})`;
            context.shadowBlur = 5;
            context.shadowColor = "#ffff33";
            context.fill();
            context.restore();
        });
    }

    onMount(() => {
        const height: number = window.innerHeight;
        const width: number = window.innerWidth;
        canvas.height = height;
        canvas.width = width;
        context = canvas.getContext("2d")!;

        for (let index = 0; index < count; index++) {
            stars.push({
                x: Math.round(Math.random() * (width - 2 * padding)) + padding,
                y: Math.round(Math.random() * (height - 2 * padding)) + padding,
                opacity: Math.random(),
                factor: 1,
                increment: Math.random() * 0.03,
            });
        }

        const animateInterval: number = setInterval(animate, 1000 / 30);

        return () => {
            clearInterval(animateInterval);
        };
    });
</script>

<canvas bind:this={canvas} />
