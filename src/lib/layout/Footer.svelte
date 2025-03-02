<script>
	import DiscordSvg from '$lib/imgs/discord.svg';
	import TwitterSvg from '$lib/imgs/x.svg';
	import LinkedInSvg from '$lib/imgs/discord.svg';
	import FacebookSvg from '$lib/imgs/discord.svg';
	import Logo2 from '$lib/components/icons/Logo2.svelte';

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
			href: 'https://discord.com',
			name: 'Discord',
			icon: DiscordSvg
		},
		{
			href: 'https://twitter.com',
			name: 'Twitter',
			icon: TwitterSvg
		},
		{
			href: 'https://linkedin.com',
			name: 'LinkedIn',
			icon: LinkedInSvg
		},
		{
			href: 'https://facebook.com',
			name: 'Facebook',
			icon: FacebookSvg
		}
	];
</script>

<footer class="relative w-full overflow-hidden bg-[#0C111D] text-gray-400">
	<!-- Header Section (from the image) -->
	<div
		class="mx-auto flex w-full max-w-screen-2xl flex-row items-center justify-between px-8 py-16"
	>
		<div class="flex flex-col gap-4">
			<h1 class="text-2xl font-bold text-white">Innovating IT solutions for the modern world.</h1>
			<p class=" text-lg text-gray-300">
				Empowering businesses with cutting-edge technology and tailored solutions.
			</p>
		</div>
		<div class="mb-12 flex gap-4">
			<a
				href="/services"
				class="rounded-full bg-white px-6 py-3 font-medium text-[#0C111D] transition-colors hover:bg-gray-200"
			>
				Discover Our Services
			</a>
			<a
				href="/contact"
				class="flex items-center gap-2 rounded-full border border-white bg-transparent px-6 py-3 font-medium text-white transition-colors hover:bg-gray-800"
			>
				Contact Us
			</a>
		</div>
	</div>

	<!-- Main Footer Content -->
	<div
		class="mx-auto flex max-w-screen-2xl flex-col p-4 px-8 py-16 text-white md:flex-row md:justify-between md:gap-8"
	>
		<!-- Logo and Description -->
		<div class="mb-12 flex flex-col gap-4 md:mb-0">
			<Logo2 />
			<p class=" mt-4 max-w-xs text-sm">
				Cache Logic is a global IT services firm committed to powering your business with innovative
				tech solutions.
			</p>
			<span class="mt-auto text-sm text-gray-500"> © 2025 Cache Logic. All rights reserved. </span>
		</div>

		<!-- Navigation Links -->
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
		<div class="mb-2 flex flex-1 items-end justify-end gap-4 sm:mb-0">
			{#each footerSocials as social}
				<a
					href={social.href}
					target="_blank"
					rel="noopener noreferrer"
					class="text-gray-400 transition-colors duration-200 hover:text-gray-200"
					aria-label={social.name}
				>
					<img src={social.icon} class="size-5" alt={social.name} />
				</a>
			{/each}
		</div>
	</div>

	<!-- Footer Bottom (Socials and Copyright) -->
	<div class="mx-auto  pb-48 max-w-screen-2xl border-t border-neutral-700/20" />

	<div
		class="pointer-events-none absolute -bottom-[50%] left-0 right-0 -translate-y-1/2 text-center text-[250px] italic text-gray-500 opacity-10"
	>
		Cache Logic
	</div>
</footer>
