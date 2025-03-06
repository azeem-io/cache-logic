<script lang="ts">
	import Ripple from '../magic/Ripple.svelte';
	import WorldMap from './WorldMap.svelte';
	import Badge from '../magic/Badge.svelte';
	import SectionHeading from './SectionHeading.svelte';
	import { Globe, HeadsetIcon, Settings } from 'lucide-svelte';

	const serviceItems = [
		{
			icon: Globe,
			title: 'Global Reach With Localized Expertise.',
			description:
				'We bring world-class IT solutions to businesses across the globe while ensuring tailored region-specific support that aligns with your unique market needs.',
			link: '#'
		},
		{
			icon: HeadsetIcon,
			title: 'Dedicated Support To Drive Your Success.',
			description:
				'Our expert team is always available to provide hands-on assistance, ensuring smooth implementation and ongoing optimization of your IT solutions.',
			link: '#'
		},
		{
			icon: Settings,
			title: 'Tailored Solutions For Every Industry.',
			description:
				"Whether you're in finance, healthcare, or e-commerce, we create customized technology solutions designed to meet your industry's challenges and goals.",
			link: '#'
		}
	];
</script>

<div class="bg-white px-4 py-16 sm:px-6 lg:px-8">
	<div class="mx-auto flex w-full flex-col items-center gap-12 text-center">
		<SectionHeading
			badgeText="Why Us"
			heading="How does Cache Logic stands out?"
			paragraph="At Cache Logic, we are a passionate team of tech experts dedicated to powering your IT
				evolution. Founded by industry leaders with diverse expertise, we focus on delivering
				innovative, reliable, and scalable tech solutions—from AI and automation to cybersecurity
				and app development. Our mission is simple: help your business stay ahead in a digital
				world."
		/>

		<img
			src="/images/meeting.png"
			alt="meeting"
			class="w-full max-w-5xl rounded-[16px] border-[#3A6EB3] shadow-2xl"
		/>

		<div class="mx-auto grid w-full max-w-7xl grid-cols-1 gap-8 text-left md:grid-cols-3">
			{#each serviceItems as item}
				<div class="flex flex-col items-center text-center text-gray-800">
					<div
						class="relative mb-4 flex h-12 w-12 items-center justify-center rounded-full border-[8px] border-[#F5F5FF] bg-[#EBECFF] text-primary"
					>
						<svelte:component this={item.icon} size={20} class="z-[900]" />
					</div>
					<!-- <div
						class="relative flex h-[100px] w-full flex-col items-center justify-center overflow-hidden rounded-lg border bg-background md:shadow-xl"
					>
					
					</div> -->
					<h3 class="mb-2 text-xl font-semibold">{item.title}</h3>
					<p class="mb-4 max-w-sm text-gray-600">{item.description}</p>
					<a
						href={item.link}
						class="flex items-center font-bold text-[#415EC6] hover:text-[#415EC6]"
					>
						Learn more
						<svg
							class="ml-1 h-4 w-4"
							xmlns="http://www.w3.org/2000/svg"
							fill="none"
							viewBox="0 0 24 24"
							stroke="currentColor"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								stroke-width="2"
								d="M14 5l7 7m0 0l-7 7m7-7H3"
							/>
						</svg>
					</a>
				</div>
			{/each}
		</div>
	</div>
</div>
