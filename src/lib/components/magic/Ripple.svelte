<script lang="ts">
	export let mainCircleSize: number = 20;
	export let mainCircleOpacity: number = 1;
	export let numCircles: number = 3;
</script>

<div
	class="absolute inset-0 flex scale-[0.8] items-center justify-center"
>
	{#each { length: numCircles } as _, i}
		<div
			class="absolute left-1/2 top-1/2 translate-x-1/2 translate-y-1/2 animate-ripple rounded-full border bg-[#667ddb] shadow-xl [--i:{i}]"
			style="width: {mainCircleSize + i * 15}px;
         height: {mainCircleSize + i * 15}px;
         opacity: {mainCircleOpacity - i * 0.38}; 
         animation-delay: {i * 0.05}s;
         border-style:{i === numCircles - 1 ? 'solid' : 'solid'};
         border-width: 0.5px;
         border-color: #000), {(5 + i * 5) / 100});
        "
		></div>
	{/each}
</div>
