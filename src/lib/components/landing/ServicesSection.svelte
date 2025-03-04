<script lang="ts">
	import SectionHeading from './SectionHeading.svelte';

	// Add the services data here
	const services = [
		{
			icon: 'brain',
			title: 'Artificial Intelligence (AI/ML)',
			description:
				'Revolutionizing decisions through intelligent solutions. We use latest AI solutions to enhance and digitalize your operations.',
			link: '#'
		},
		{
			icon: 'bolt',
			title: 'Automation',
			description: 'Streamlining processes for greater efficiency.',
			link: '#',
			highlighted: true
		},
		{
			icon: 'shield',
			title: 'Cybersecurity',
			description: 'Protecting your business from evolving threats.',
			link: '#'
		},
		{
			icon: 'customize',
			title: 'Custom Solutions',
			description: 'Tech built uniquely for your needs.',
			link: '#'
		},
		{
			icon: 'code',
			title: 'DevOps',
			description: 'Optimizing development and deployment pipelines.',
			link: '#'
		},
		{
			icon: 'mobile',
			title: 'Web & Mobile Apps',
			description:
				'Building high-performance, user-friendly applications tailored to your business needs. From sleek mobile experiences to robust web platforms, we ensure seamless functionality and scalability.',
			link: '#'
		}
	];
</script>

<div class="bg-white px-4 py-16 sm:px-6 lg:px-8">
	<div class="mx-auto flex w-full flex-col items-center gap-12 text-center">
		<SectionHeading
			badgeText="Our Services"
			heading="Services We Offer"
			paragraph="Powerful, self-serve product and growth analytics to help you convert, engage, and retain more users."
		/>

		<!-- Services grid -->
		<div class="grid w-full max-w-7xl grid-cols-1 gap-6 md:grid-cols-2 lg:grid-cols-3">
			{#each services as service, i}
				<div
					class={`flex flex-col items-start rounded-lg p-8 text-left ${service.highlighted ? 'bg-blue-900 text-white' : 'bg-gray-50'}`}
				>
					<!-- Icon -->
					<div
						class={`mb-5 rounded-lg p-3 ${service.highlighted ? 'bg-white' : 'bg-blue-600 text-white'}`}
					>
						{#if service.icon === 'brain'}
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="h-6 w-6"
								fill="none"
								viewBox="0 0 24 24"
								stroke="currentColor"
							>
								<path
									stroke-linecap="round"
									stroke-linejoin="round"
									stroke-width="2"
									d="M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"
								/>
							</svg>
						{:else if service.icon === 'bolt'}
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="h-6 w-6"
								fill="none"
								viewBox="0 0 24 24"
								stroke="currentColor"
							>
								<path
									stroke-linecap="round"
									stroke-linejoin="round"
									stroke-width="2"
									d="M13 10V3L4 14h7v7l9-11h-7z"
								/>
							</svg>
						{:else if service.icon === 'shield'}
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="h-6 w-6"
								fill="none"
								viewBox="0 0 24 24"
								stroke="currentColor"
							>
								<path
									stroke-linecap="round"
									stroke-linejoin="round"
									stroke-width="2"
									d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z"
								/>
							</svg>
						{:else if service.icon === 'customize'}
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="h-6 w-6"
								fill="none"
								viewBox="0 0 24 24"
								stroke="currentColor"
							>
								<path
									stroke-linecap="round"
									stroke-linejoin="round"
									stroke-width="2"
									d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z"
								/>
								<path
									stroke-linecap="round"
									stroke-linejoin="round"
									stroke-width="2"
									d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"
								/>
							</svg>
						{:else if service.icon === 'code'}
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="h-6 w-6"
								fill="none"
								viewBox="0 0 24 24"
								stroke="currentColor"
							>
								<path
									stroke-linecap="round"
									stroke-linejoin="round"
									stroke-width="2"
									d="M8 9l3 3-3 3m5 0h3M5 20h14a2 2 0 002-2V6a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"
								/>
							</svg>
						{:else if service.icon === 'mobile'}
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="h-6 w-6"
								fill="none"
								viewBox="0 0 24 24"
								stroke="currentColor"
							>
								<path
									stroke-linecap="round"
									stroke-linejoin="round"
									stroke-width="2"
									d="M12 18h.01M8 21h8a2 2 0 002-2V5a2 2 0 00-2-2H8a2 2 0 00-2 2v14a2 2 0 002 2z"
								/>
							</svg>
						{/if}
					</div>

					<!-- Content -->
					<h3 class="mb-3 text-xl font-bold">{service.title}</h3>
					<p class="mb-6">{service.description}</p>

					<!-- View Service link -->
					<a
						href={service.link}
						class="mt-auto inline-flex items-center text-blue-600 hover:underline"
					>
						<span class={service.highlighted ? 'text-white' : ''}>View Service</span>
						<svg
							xmlns="http://www.w3.org/2000/svg"
							class="ml-1 h-5 w-5"
							viewBox="0 0 20 20"
							fill="currentColor"
						>
							<path
								fill-rule="evenodd"
								d="M10.293 5.293a1 1 0 011.414 0l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414-1.414L12.586 11H5a1 1 0 110-2h7.586l-2.293-2.293a1 1 0 010-1.414z"
								clip-rule="evenodd"
							/>
						</svg>
					</a>
				</div>
			{/each}
		</div>
	</div>
</div>
