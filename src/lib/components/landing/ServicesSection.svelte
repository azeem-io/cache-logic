<script lang="ts">
	import { ArrowRight, Container, ShieldCheck } from 'lucide-svelte';
	import SectionHeading from './SectionHeading.svelte';
	import ChartIcon from '../svgs/ChartIcon.svelte';
	import ZapIcon from '../svgs/ZapIcon.svelte';
	import MessageIcon from '../svgs/MessageIcon.svelte';
	import ChatIcon from '../svgs/ChatIcon.svelte';
	import { goto } from '$app/navigation';
	import { inview } from 'svelte-inview';
	import type { ObserverEventDetails } from 'svelte-inview';

	// Track which cards are in view
	let visibleCards = new Array(6).fill(false);

	const handleCardInView =
		(index: number) =>
		({ detail }: CustomEvent<ObserverEventDetails>) => {
			if (detail.inView) {
				visibleCards[index] = true;
			}
		};

	const services = [
		{
			icon: ChatIcon,
			title: 'Artificial Intelligence (AI/ML)',
			description:
				'Revolutionizing decisions through intelligent solutions. We use latest AI solutions to enhance and digitalize your operations.',
			link: '/intelligence',
			colSpan: true // This card spans 2 columns
		},
		{
			icon: ZapIcon,
			title: 'Automation',
			description: 'Streamlining processes for greater efficiency.',
			link: '/automation'
		},
		{
			icon: ShieldCheck,
			title: 'Cybersecurity',
			description: 'Protecting your business from evolving threats.',
			link: '/cybersecurity'
		},
		{
			icon: ChartIcon,
			title: 'Custom Solutions',
			description: 'Tech built uniquely for your needs.',
			link: '/solutions'
		},
		{
			icon: Container,
			title: 'DevOps',
			description: 'Optimizing development and deployment pipelines.',
			link: '/dev-ops'
		},
		{
			icon: MessageIcon,
			title: 'Web & Mobile Apps',
			description:
				'Building high-performance, user-friendly applications tailored to your business needs. From sleek mobile experiences to robust web platforms, we ensure seamless functionality and scalability.',
			link: '/web-dev',
			colSpan: true // This card spans 2 columns
		}
	];
</script>

<div class="px-4 py-16 sm:px-6 lg:px-8">
	<div class="mx-auto flex w-full flex-col items-center gap-12 text-center">
		<SectionHeading
			badgeText="Our Services"
			heading="Services We Offer"
			paragraph="Powerful, self-serve product and growth analytics to help you convert, engage, and retain more users."
		/>

		<div class="grid w-full max-w-7xl grid-cols-1 gap-8 md:grid-cols-2 lg:grid-cols-4">
			{#each services as service, i}
				<div
					use:inview={{
						unobserveOnEnter: true,
						rootMargin: '-80px'
					}}
					on:inview_change={handleCardInView(i)}
					class="group h-full w-full {service.colSpan ? 'md:col-span-2' : ''}"
				>
					<button
						on:click={() => goto(service.link)}
						class={` flex h-full w-full flex-col items-start rounded-lg bg-[#F9FAFB] p-8 text-left antialiased transition-all duration-300 ease-out group-hover:-translate-y-2 group-hover:bg-[#1D315F] group-hover:text-white group-hover:shadow-[0px_8px_32px_rgba(29,57,102,0.6)]

 ${visibleCards[i] ? 'card-animated' : 'opacity-0'}`}
						style={`animation-delay: ${i * 150}ms;`}
					>
						<div
							class={`mb-5 rounded-lg bg-primary p-3 text-white transition-all duration-300 ease-out group-hover:bg-white group-hover:text-primary`}
						>
							<svelte:component this={service.icon} />
						</div>

						<h3 class="mb-3 text-xl font-bold antialiased">{service.title}</h3>
						<p class="mb-6 antialiased">{service.description}</p>

						<p
							class="mt-auto inline-flex items-center font-bold text-primary transition-all duration-300 ease-out hover:underline group-hover:text-white"
						>
							<span>View Service</span>
							<ArrowRight
								size={16}
								class="duration-[350] ml-1 text-current transition-transform group-hover:translate-x-1"
							/>
						</p>
					</button>
				</div>
			{/each}
		</div>
	</div>
</div>

<style>
	@keyframes fadeInUp {
		from {
			opacity: 0;
			transform: translateY(20px);
		}
		to {
			opacity: 1;
			transform: translateY(0);
		}
	}

	.card-animated {
		animation: fadeInUp 1.5s cubic-bezier(0.22, 1, 0.36, 1) forwards;
		opacity: 0;
	}
</style>
