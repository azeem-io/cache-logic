<script lang="ts">
	import Badge from '../magic/Badge.svelte';

	export let badgeText: string;
	export let heading: string;
	export let paragraph: string;
	export let align: 'center' | 'left' = 'center';
</script>

<div class=" flex flex-col {align === 'center' ? 'items-center' : 'items-start'} gap-4 md:gap-6">
	<Badge>{badgeText}</Badge>
	<h2
		class="-mt-1 text-3xl font-semibold text-gray-900 md:-mt-3 md:text-4xl {align === 'left'
			? 'text-left'
			: 'text-center'}"
	>
		{heading}
	</h2>
	<p
		class="{align === 'center'
			? 'mx-auto text-center'
			: 'text-left'} max-w-3xl text-sm text-gray-600 md:text-xl"
	>
		{paragraph}
	</p>
</div>
