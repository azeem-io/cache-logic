<script>
	import { goto } from '$app/navigation';
	import { page } from '$app/state';
	import { Button } from '$lib/components/ui/button';
</script>

<div class="flex h-screen flex-col items-center justify-center">
	<h1 class="text-balance text-center text-9xl font-bold text-red-600">
		{page.status}
	</h1>
	<p class="text-5xl font-semibold">{page.error?.message ?? 'Unknow Error Occured'}</p>
	<Button
		on:click={() => {
			goto('/');
		}}
		class="mt-6">Back To Home</Button
	>
</div>
