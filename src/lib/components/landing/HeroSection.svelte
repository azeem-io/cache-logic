<script lang="ts">
	import { ArrowRightIcon } from 'lucide-svelte';
	import AnimatedShinyText from '$lib/components/magic/AnimatedShinyText/AnimatedShinyText.svelte';
	import BorderBeam from '$lib/components/magic/borderbeam/BorderBeam.svelte';
	import Button from '$lib/components/ui/button/button.svelte';
	import type { ObserverEventDetails } from 'svelte-inview';
	import { inview } from 'svelte-inview';

	// Images
	import HeroDarkImg from '$lib/imgs/hero-dark.png';
	import HeroLightImg from '$lib/imgs/hero-light.png';
	let inView = false;
	const handleChange = ({ detail }: CustomEvent<ObserverEventDetails>) => {
		// console.log(detail);
		inView = detail.inView;
	};
</script>

<section id="hero" class="relative mx-auto mt-20 h-screen px-6 md:px-8">
	<div
		class=" absolute left-1/2 top-44 z-[0] flex h-[70%] w-[92%] -translate-x-1/2 flex-col rounded-2xl bg-[#27538E]"
	></div>

	<div
		class="relative z-[100] flex h-[85%] flex-col justify-center rounded-2xl bg-[#1D315F] bg-[url('/images/hero.webp')] bg-cover bg-center p-16 shadow-2xl"
	>
		<h1
			class="animate-fade-in text-balance bg-gradient-to-br from-black from-30% to-black/40 bg-clip-text py-6 text-left text-5xl font-bold text-transparent text-white opacity-0 [--animation-delay:200ms] dark:from-white dark:to-white/40 sm:text-3xl md:text-5xl lg:text-6xl"
		>
			Fast-Tracking Your AI
			<br class="hidden md:block" />
			{' '}
			Evolution
		</h1>
		<p
			class="mb-12 animate-fade-in max-w-lg text-lg tracking-tight text-[#D9D9D9] opacity-0 [--animation-delay:400ms] md:text-xl"
		>
			Empowering businesses with cutting-edge technology and tailored solutions.
		</p>
		<Button
			variant="secondary"
			class="w-fit animate-fade-in gap-1 rounded-lg  opacity-0 ease-in-out [--animation-delay:600ms]"
		>
			<span>Get Started for free </span>
			<ArrowRightIcon
				class="ml-1 size-4 transition-transform duration-300 ease-in-out group-hover:translate-x-1"
			/>
		</Button>
	</div>

	<!-- <div
		use:inview={{
			unobserveOnEnter: true,
			rootMargin: '-100px'
		}}
		on:inview_change={handleChange}
		class="relative mt-32 animate-fade-up opacity-0 [--animation-delay:400ms] [perspective:2000px] after:absolute after:inset-0 after:z-50 after:[background:linear-gradient(to_top,hsl(var(--background))_30%,transparent)]"
	>
		<div
			class="rounded-xl border border-white/10 bg-white bg-opacity-[0.01] before:absolute before:bottom-1/2 before:left-0 before:top-0 before:size-full before:opacity-0 before:[background-image:linear-gradient(to_bottom,var(--color-one),var(--color-one),transparent_40%)] before:[filter:blur(180px)] {inView
				? 'before:animate-image-glow'
				: ''}"
		>
			<BorderBeam
				size={200}
				duration={12}
				delay={0}
				colorFrom="var(--color-one)"
				colorTo="var(--color-two)"
			/>

			<img
				src={HeroDarkImg}
				alt="HeroDarkImage"
				class="relative hidden size-full rounded-[inherit] border object-contain dark:block"
			/>
			<img
				src={HeroLightImg}
				alt="HeroLightImage"
				class="relative block size-full rounded-[inherit] border object-contain dark:hidden"
			/>
		</div>
	</div> -->
</section>
