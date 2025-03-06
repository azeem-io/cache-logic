<script lang="ts">
	import Logo2 from '$lib/components/svgs/Logo2.svelte';
	import NavLinks from '$lib/components/magic/NavLinks.svelte';
	import Button from '$lib/components/ui/button/button.svelte';
	import { cn } from '$lib/utils';
	import { AlignJustify, XIcon } from 'lucide-svelte';
	import { fly } from 'svelte/transition';

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
</script>

<svelte:window bind:innerWidth />
<header
	class="fixed left-0 top-0 z-[999] w-full -translate-y-4 animate-fade-in border-b bg-white opacity-0 backdrop-blur-md"
>
	<!-- {#if innerWidth < 768} -->
	<div class="container flex h-14 items-center justify-between">
		<!-- <a class="text-md flex items-center" href="/"> Cache Logic </a> -->
		<Logo2 />
		<div class="hidden w-full items-center justify-between md:flex">
			<NavLinks />
			<div class="ml-auto hidden h-full items-center md:flex">
				<Button
					class="mr-6 text-sm"
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
			<button class="ml-6 md:hidden" use:toggleOverflowHidden>
				<span class="sr-only">Toggle menu</span>
				{#if hamburgerMenuIsOpen}
					<XIcon strokeWidth={1.4} class="text-gray-300" />
				{:else}
					<AlignJustify strokeWidth={1.4} class="text-gray-300" />
				{/if}
			</button>
		</div>
		<!-- {/if} -->
	</div>
</header>

<nav
	class={cn(
		`fixed left-0  top-0 z-[999] h-screen w-full overflow-auto `,
		{
			'pointer-events-none': !hamburgerMenuIsOpen
		},
		{
			'bg-background/70 backdrop-blur-md': hamburgerMenuIsOpen
		}
	)}
>
	{#if hamburgerMenuIsOpen === true}
		<div class="container flex h-14 items-center justify-between">
			<Logo2 />

			<button class="md:hidden" use:toggleOverflowHidden>
				<span class="sr-only">Toggle menu</span>
				{#if hamburgerMenuIsOpen}
					<XIcon strokeWidth={1.4} class="text-gray-300" />
				{:else}
					<AlignJustify strokeWidth={1.4} class="text-gray-300" />
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
