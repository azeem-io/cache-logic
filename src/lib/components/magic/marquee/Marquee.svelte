<script lang="ts">
	import { cn } from '$lib/utils';
	export let pauseOnHover: boolean = false;
	export let vertical: boolean = false;
	export let repeat: number = 6;
	export let reverse: boolean = false;

	let className: any = '';
	export { className as class };
</script>

<div
	class={cn(
		'group relative mx-auto flex max-w-7xl overflow-hidden [--duration:30s] [--gap:2rem] [gap:var(--gap)]  md:p-2 md:[--gap:4rem]',
		{
			'flex-row': !vertical,
			'flex-col': vertical
		},
		className
	)}
	style="mask-image: linear-gradient(to right, transparent, white 20%, white 80%, transparent);"
>
	{#each { length: repeat } as _, i (i)}
		<div
			class={cn('flex shrink-0 justify-around [gap:var(--gap)]', {
				'animate-marquee flex-row': !vertical,
				'animate-marquee-vertical flex-col': vertical,
				'group-hover:[animation-play-state:paused]': pauseOnHover,
				'[animation-direction:reverse]': reverse
			})}
		>
			<slot>Default</slot>
		</div>
	{/each}
</div>
