<script lang="ts">
	import Badge from '../magic/Badge.svelte';

	export let badgeText: string;
	export let heading: string;
	export let paragraph: string;
</script>

<div class="flex flex-col items-center gap-6">
	<Badge>{badgeText}</Badge>
	<h2 class=" text-4xl font-semibold text-gray-900">{heading}</h2>
	<p class="mx-auto max-w-3xl text-xl text-gray-600">
		{paragraph}
	</p>
</div>
