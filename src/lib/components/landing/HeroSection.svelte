<script lang="ts">
	import { ArrowRightIcon } from 'lucide-svelte';
	import Button from '$lib/components/ui/button/button.svelte';
	import { fly } from 'svelte/transition';
	import { onMount } from 'svelte';
	import { cubicOut } from 'svelte/easing';

	let mounted = false;
	onMount(() => {
		mounted = true;
	});
</script>

<section id="hero" class="relative mx-auto mt-[4.5rem] h-fit px-4 md:px-8">
	{#if mounted}
		<div
			transition:fly={{ y: -60, delay: 200, duration: 400, easing: cubicOut }}
			class=" absolute left-1/2 top-[6vh] z-[0] flex h-[77vh] w-[88%] -translate-x-1/2 flex-col rounded-2xl bg-[#27538E] md:h-[80vh] md:w-[92%]"
		></div>

		<div
			transition:fly={{ y: 50, easing: cubicOut }}
			class="relative z-[100] flex h-[80vh] flex-col justify-center rounded-2xl bg-[#1D315F] bg-[url('/images/hero.webp')] bg-cover bg-center p-6 shadow-2xl md:h-[83vh] md:p-16"
		>
			<h1
				transition:fly={{ y: 30, delay: 180, duration: 400 }}
				class="text-balance bg-gradient-to-br from-black from-30% to-black/40 bg-clip-text py-6 text-left text-5xl font-bold text-transparent text-white dark:from-white dark:to-white/40 sm:text-3xl md:text-5xl lg:text-6xl"
			>
				Fast-Tracking Your AI
				<br class="hidden md:block" />
				{' '}
				Evolution
			</h1>
			<p
				transition:fly={{ y: 30, delay: 180, duration: 400 }}
				class="mb-12 max-w-lg text-lg tracking-tight text-[#D9D9D9] md:text-xl"
			>
				Empowering businesses with cutting-edge technology and tailored solutions.
			</p>
			<div transition:fly={{ y: 30, delay: 180, duration: 400 }}>
				<Button variant="secondary" class="w-fit  gap-1 rounded-lg   ease-in-out ">
					<span>Get Started for free </span>
					<ArrowRightIcon
						class="ml-1 size-4 transition-transform duration-300 ease-in-out group-hover:translate-x-1"
					/>
				</Button>
			</div>
		</div>
	{/if}
</section>
