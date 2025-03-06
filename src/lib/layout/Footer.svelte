<script>
	import FacebookIcon from '$lib/components/svgs/FacebookIcon.svelte';
	import GithubIcon from '$lib/components/svgs/GithubIcon.svelte';
	import LinkedinIcon from '$lib/components/svgs/LinkedinIcon.svelte';
	import Button from '$lib/components/ui/button/button.svelte';

	import Logo2 from '$lib/components/svgs/Logo2.svelte';
	import TwitterIcon from '$lib/components/svgs/TwitterIcon.svelte';
	import { Phone } from 'lucide-svelte';
	import LogoText from '$lib/components/svgs/LogoText.svelte';

	const footerNavs = [
		{
			label: 'Company',
			items: [
				{
					href: '/',
					name: 'About us'
				},
				{
					href: '/careers',
					name: 'Careers'
				},
				{
					href: '/news',
					name: 'News'
				},
				{
					href: '/contact',
					name: 'Contact'
				}
			]
		}
	];

	const footerSocials = [
		{
			href: 'https://x.com',
			name: 'X',
			icon: TwitterIcon
		},
		{
			href: 'https://linkedin.com',
			name: 'Linkedin',
			icon: LinkedinIcon
		},
		{
			href: 'https://facebook.com',
			name: 'Facebook',
			icon: FacebookIcon
		},
		{
			href: 'https://github.com',
			name: 'Github',
			icon: GithubIcon
		}
	];
</script>

<footer class="relative w-full overflow-hidden bg-[#0C111D] text-gray-400">
	<!-- Header Section (from the image) -->
	<div
		class="mx-auto flex w-full max-w-screen-2xl flex-col items-start justify-between px-8 py-12 pb-16 md:flex-row md:py-16"
	>
		<div class="flex flex-col gap-4">
			<h1 class="text-3xl font-semibold text-white">
				Innovating IT solutions for the modern world.
			</h1>
			<p class=" mb-6 text-xl text-gray-300">
				Empowering businesses with cutting-edge technology and <br /> tailored solutions.
			</p>
		</div>
		<div class="flex w-full flex-col gap-4 md:mb-12 md:w-auto md:flex-row">
			<Button size="lg" variant="secondary" href="/services">Discover Our Services</Button>
			<Button size="lg" variant="ghost" class="border text-white" href="/contact"
				><Phone size={16} class="mr-1.5" /> Contact Us</Button
			>
		</div>
	</div>

	<div class="mx-auto max-w-screen-2xl border-t border-neutral-700/30 pb-1" />

	<div
		class="mx-auto flex max-w-screen-2xl flex-col p-4 px-8 py-16 pb-12 text-white md:flex-row md:justify-between md:gap-8"
	>
		<div class="mb-12 flex flex-col gap-4 md:mb-0">
			<Logo2 />
			<p class=" mt-4 max-w-xs text-sm">
				Cache Logic is a global IT services firm committed to powering your business with innovative
				tech solutions.
			</p>
			<span class="mt-auto text-sm text-gray-500"> © 2025 Cache Logic. All rights reserved. </span>
		</div>

		<div class="grid grid-cols-1 gap-8 sm:grid-cols-1 md:grid-cols-1">
			{#each footerNavs as nav}
				<div>
					<h2 class="mb-4 text-sm font-normal text-gray-300">
						{nav.label}
					</h2>
					<ul class="grid gap-3">
						{#each nav.items as item}
							<li>
								<a
									href={item.href}
									class=" font-bold text-white transition-colors duration-200 hover:text-gray-200"
								>
									{item.name}
								</a>
							</li>
						{/each}
					</ul>
				</div>
			{/each}
		</div>
		<div class=" mt-8 flex flex-1 items-end gap-4 sm:mb-0 md:justify-end">
			{#each footerSocials as social}
				<a
					href={social.href}
					target="_blank"
					rel="noopener noreferrer"
					class="text-gray-400 transition-colors duration-200 hover:text-gray-200"
					aria-label={social.name}
				>
					<svelte:component this={social.icon} />
				</a>
			{/each}
		</div>
	</div>
	<div class="mx-auto max-w-screen-2xl border-t border-neutral-700/20 pb-8" />
	<LogoText />
</footer>
