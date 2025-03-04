<script lang="ts">
	import { Motion, AnimatePresence } from 'svelte-motion';
	let selected = 0;
	let dir: any;

	let TABS = [
		{
			id: 1,
			title: 'Services',
			links: [
				{
					name: 'Artificial Intel',
					link: '/ai'
				},
				{
					name: 'Web Development',
					link: '/web-dev'
				},
				{
					name: 'Cloud Solutions',
					link: '/cloud'
				}
			]
		},
		{
			id: 2,
			title: 'About us',
			links: [
				{
					name: 'Our Team',
					link: '/team'
				},
				{
					name: 'Company History',
					link: '/history'
				},
				{
					name: 'Contact Us',
					link: '/contact'
				}
			]
		}
	];

	let left: any;
	let moveNub = (node: HTMLElement) => {
		if (selected) {
			const hoveredTab = document.getElementById(`shift-tab-${selected}`);
			const overlayContent = document.getElementById('overlay-content');

			if (!hoveredTab || !overlayContent) return;
			console.log(hoveredTab, overlayContent, 'Hovered Tab');

			const tabRect = hoveredTab.getBoundingClientRect();
			const { left: contentLeft } = overlayContent.getBoundingClientRect();

			const tabCenter = tabRect.left + tabRect.width / 2 - contentLeft;

			left = tabCenter;
		}
	};

	let handleSetSelected = (val: any) => {
		// console.log({ val, selected });
		if (typeof selected === 'number' && typeof val === 'number') {
			dir = selected > val ? 'r' : 'l';
		} else if (val === null) {
			dir = null;
		}
		selected = val;
		moveNub();
	};
</script>

<a
	href="/"
	class="ml-8 px-3 py-1.5 text-sm font-bold text-gray-600 transition-colors hover:text-gray-900"
	>Home</a
>
<!-- svelte-ignore a11y-no-static-element-interactions -->
<div on:mouseleave={() => handleSetSelected(null)} class="relative flex h-fit gap-2">
	{#each TABS as item (item)}
		<button
			id="shift-tab-{item.id}"
			on:click={() => handleSetSelected(item.id)}
			on:mouseenter={() => handleSetSelected(item.id)}
			class={`flex items-center gap-1 rounded-full px-3 py-1.5 text-sm font-bold transition-colors ${
				selected === item.id ? '  text-gray-900' : 'text-gray-600'
			}`}
		>
			<span>
				{item.title}
			</span>
			<svg
				xmlns="http://www.w3.org/2000/svg"
				width="16"
				height="16"
				viewBox="0 0 24 24"
				fill="none"
				stroke="currentColor"
				stroke-width="1.4"
				stroke-linecap="round"
				stroke-linejoin="round"
				class={`transition-transform ${selected === item.id ? 'rotate-180' : ''}`}
				><path d="m6 9 6 6 6-6" /></svg
			>
		</button>
	{/each}
	<AnimatePresence
		let:item
		list={[
			{ key: 1, id: 1 },
			{ key: 2, id: 2 }
		]}
	>
		{#if selected}
			<Motion
				initial={{
					opacity: 0,
					y: 8
				}}
				animate={{
					opacity: 1,
					y: 0
				}}
				exit={{
					opacity: 0,
					y: 8
				}}
				let:motion
			>
				<div
					id="overlay-content"
					class="absolute left-0 top-[calc(100%_+_24px)] z-40 w-64 rounded-lg border border-black/20 bg-white bg-gradient-to-b py-4"
					use:motion
				>
					<div class="absolute -top-[24px] left-0 right-0 h-[40px]" />
					<Motion animate={{ left }} transition={{ duration: 0.25, ease: 'easeInOut' }} let:motion>
						<span
							style="clip-path: polygon(0 0, 100% 0, 50% 50%, 0% 100%);"
							class="absolute left-1/2 top-0 h-4 w-4 -translate-x-1/2 -translate-y-1/2 rotate-45 rounded-tl border border-black/20 bg-white"
							use:motion
							use:moveNub
						>
						</span>
					</Motion>
					{#each TABS as item}
						<div class="overflow-hidden">
							{#if selected === item.id}
								<Motion
									initial={{
										opacity: 0,
										x: dir === 'l' ? 100 : dir === 'r' ? -100 : 0
									}}
									animate={{ opacity: 1, x: 0 }}
									transition={{ duration: 0.25, ease: 'easeInOut' }}
									let:motion
								>
									<div use:motion class="flex flex-col gap-1">
										{#each TABS.find((tab) => tab.id === selected)?.links || [] as link}
											<a
												href={link.link}
												class="px-4 py-2 text-sm transition-colors duration-200 hover:bg-slate-200 hover:text-black"
											>
												{link.name}
											</a>
										{/each}
									</div>
								</Motion>
							{/if}
						</div>
					{/each}
				</div>
			</Motion>
		{/if}
	</AnimatePresence>
</div>

<a
	href="/contact"
	class="px-3 py-1.5 text-sm font-bold text-gray-600 transition-colors hover:text-gray-900"
	>Contact</a
>
