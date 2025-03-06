<script lang="ts">
	import Logo2 from '$lib/components/svgs/Logo2.svelte';
	import NavLinks from '$lib/components/magic/NavLinks.svelte';
	import Button from '$lib/components/ui/button/button.svelte';
	import { cn } from '$lib/utils';
	import { AlignJustify, XIcon } from 'lucide-svelte';
	import { fly } from 'svelte/transition';
	import { onMount } from 'svelte';

	const menuItem = [
		{
			id: 1,
			label: 'Services',
			href: '#'
		},
		{
			id: 2,
			label: 'About Us',
			href: '#'
		},
		{
			id: 3,
			label: 'Contact',
			href: '#'
		}
	];

	let hamburgerMenuIsOpen = false;
	let scrollY = 0;
	let hasScrolled = false;

	function toggleOverflowHidden(node: HTMLElement) {
		node.addEventListener('click', () => {
			hamburgerMenuIsOpen = !hamburgerMenuIsOpen;
			const html = document.querySelector('html');
			if (html) {
				if (hamburgerMenuIsOpen) {
					html.classList.add('overflow-hidden');
				} else {
					html.classList.remove('overflow-hidden');
				}
			}
		});
	}
	
	let innerWidth = 0;

	// Handle scroll events
	function handleScroll() {
		// Only update when crossing the threshold to prevent unnecessary rerenders
		const shouldHaveScrolled = scrollY > 20;
		if (hasScrolled !== shouldHaveScrolled) {
			hasScrolled = shouldHaveScrolled;
		}
	}

	// Add a reactive statement to ensure scrollY changes always update hasScrolled
	$: {
		hasScrolled = scrollY > 20;
	}

	onMount(() => {
		// Initial check on mount
		hasScrolled = window.scrollY > 20;
		
		// Add a more direct scroll listener as a backup
		window.addEventListener('scroll', () => {
			hasScrolled = window.scrollY > 20;
		}, { passive: true });
		
		return () => {
			window.removeEventListener('scroll', () => {
				hasScrolled = window.scrollY > 20;
			});
		};
	});
</script>

<svelte:window bind:innerWidth bind:scrollY on:scroll={handleScroll} />

<header
	class={cn(
		"fixed left-0 top-0 z-[999] w-full -translate-y-4 animate-fade-in opacity-0 transition-colors duration-300",
		hasScrolled ? "bg-white border-b" : "bg-transparent"
	)}
>
	<div
		class="container mx-auto flex h-14 max-w-screen-2xl items-center justify-between px-6 md:px-8"
	>
		<Logo2 />
		<div class="hidden w-full items-center justify-between md:flex">
			<NavLinks />
			<div class="ml-auto hidden h-full items-center md:flex">
				<Button
					class="text-sm"
					on:click={() => {
						const contactSection = document.getElementById('contact-section');
						if (contactSection) {
							contactSection.scrollIntoView({ behavior: 'smooth' });
						}
					}}
				>
					Contact Us
				</Button>
			</div>
		</div>
		<button class="ml-6 md:hidden" use:toggleOverflowHidden>
			<span class="sr-only">Toggle menu</span>
			{#if hamburgerMenuIsOpen}
				<XIcon strokeWidth={1.4} class="text-gray-900" />
			{:else}
				<AlignJustify strokeWidth={1.4} class="text-gray-900" />
			{/if}
		</button>
	</div>
</header>

<nav
	class={cn(
		`fixed left-0 top-0 z-[999] h-screen w-full overflow-auto`,
		{
			'pointer-events-none': !hamburgerMenuIsOpen
		},
		{
			'bg-background/70 backdrop-blur-md': hamburgerMenuIsOpen
		}
	)}
>
	{#if hamburgerMenuIsOpen === true}
		<div class="container mx-auto flex h-14 max-w-screen-2xl items-center justify-between px-6">
			<Logo2 />

			<button class="md:hidden" use:toggleOverflowHidden>
				<span class="sr-only">Toggle menu</span>
				{#if hamburgerMenuIsOpen}
					<XIcon strokeWidth={1.4} class="text-gray-900" />
				{:else}
					<AlignJustify strokeWidth={1.4} class="text-gray-900" />
				{/if}
			</button>
		</div>
		<ul
			in:fly={{ y: -30, duration: 400 }}
			class="flex flex-col uppercase ease-in md:flex-row md:items-center md:normal-case"
		>
			{#each menuItem as item, i}
				<li class="border-grey-dark border-b py-0.5 pl-6 md:border-none">
					<a
						class="hover:text-grey flex h-[var(--navigation-height)] w-full items-center text-xl transition-[color,transform] duration-300 md:translate-y-0 md:text-sm md:transition-colors {hamburgerMenuIsOpen
							? '[&_a]:translate-y-0'
							: ''}"
						href={item.href}
					>
						{item.label}
					</a>
				</li>
			{/each}
		</ul>
	{/if}
</nav>