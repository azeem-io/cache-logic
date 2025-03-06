<script lang="ts">
	import SectionHeading from './SectionHeading.svelte';
	import { Button } from '$lib/components/ui/button';
	import LinePattern from '../svgs/LinePattern.svelte';
	import PlayIcon from '../svgs/PlayIcon.svelte';
	import { inview } from 'svelte-inview';
	import type { ObserverEventDetails } from 'svelte-inview';

	let visibleProjects = new Array(3).fill(false);

	const handleProjectInView =
		(index: number) =>
		({ detail }: CustomEvent<ObserverEventDetails>) => {
			if (detail.inView) {
				visibleProjects[index] = true;
			}
		};

	const projects = [
		{
			id: 1,
			title: 'Product # 1',
			description:
				'Whether you have a team of 2 or 200, our shared team inboxes keep everyone on the same page and in the loop. Leverage automation to move fast, while always giving customers a human, helpful experience.',
			image: '/images/project.png'
		},
		{
			id: 2,
			title: 'Product # 2',
			description:
				'Keep your customers in the flow by embedding help articles right on your website. With Beacon, they never have to leave the page to find an answer.',
			image: '/images/project.png'
		},
		{
			id: 3,
			title: 'Product # 3',
			description:
				"Measure what matters with Untitled's easy-to-use reports. You can filter, export, and drilldown on the data in a couple clicks.",
			image: '/images/project.png'
		}
	];
</script>

<div class="bg-white px-4 py-24 sm:px-6 lg:px-8">
	<div class="mx-auto w-full max-w-7xl">
		<SectionHeading
			badgeText="Our Portfolio"
			heading="Products We Have Worked On"
			paragraph="Powerful, self-serve product and growth analytics to help you convert, engage, and retain more users. Trusted by over 4,000 startups."
		/>

		<div class="mt-20 flex flex-col gap-24">
			{#each projects as project, i}
				<div
					class="relative flex flex-col-reverse items-center gap-6 md:gap-24 lg:flex-row lg:items-start {i %
						2 ===
					1
						? 'lg:flex-row-reverse'
						: ''}"
				>
					<div class="flex flex-1 flex-col gap-4 lg:gap-6 lg:pr-20">
						<h3 class="text-2xl font-bold text-gray-900">{project.title}</h3>
						<p class="max-w-md text-gray-600">{project.description}</p>
						<div class="flex gap-4">
							<Button variant="outline" class="w-full items-center gap-1 lg:w-auto">
								<PlayIcon />
								Demo
							</Button>
							<Button class="w-full lg:w-auto">Learn more</Button>
						</div>
					</div>

					<div class="relative flex-1 rounded-2xl bg-gray-100 p-10">
						<div
							use:inview={{
								unobserveOnEnter: true,
								rootMargin: '-80px'
							}}
							on:inview_change={handleProjectInView(i)}
							class="relative z-[100] overflow-hidden rounded-lg border-[4px] border-gray-900 shadow-lg
                            {visibleProjects[i] ? 'image-animated' : 'opacity-0'}"
							style={`animation-delay: ${i * 150}ms;`}
						>
							<img
								src={project.image}
								alt={project.title}
								class=" h-auto w-full rounded-md object-cover"
							/>
						</div>
						<div
							class="absolute {i % 2 === 0
								? '-right-32'
								: '-left-32'} top-[30%] z-[50] hidden -translate-y-1/2 transform lg:block"
						>
							<LinePattern />
						</div>
					</div>
				</div>
			{/each}
		</div>
	</div>
</div>

<style>
	.image-animated {
		animation: fadeInUp 1.5s cubic-bezier(0.22, 1, 0.36, 1) forwards;
		opacity: 0;
	}

	@keyframes fadeInUp {
		0% {
			opacity: 0;
			transform: translateY(30px);
		}
		100% {
			opacity: 1;
			transform: translateY(0);
		}
	}
</style>
