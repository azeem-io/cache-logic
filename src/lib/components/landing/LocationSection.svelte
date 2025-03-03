<script lang="ts">
	import { AnimatePresence, Motion, useMotionValue, useSpring, useTransform } from 'svelte-motion';
	import Ripple from '../magic/Ripple.svelte';
	import WorldMap from './WorldMap.svelte';
	import Badge from '../magic/Badge.svelte';
	import * as Tooltip from '$lib/components/ui/tooltip';

	const locations = [
		{
			country: 'United States',
			address: 'Building X, Street Y, Baltimore MD'
		},
		{
			country: 'Pakistan',
			address: 'Building X, Street Y, Lahore PK'
		}
	];

	let markers = [
		{ id: 'us', x: 170, y: 215, label: 'United States' },
		{ id: 'pk', x: 695, y: 230, label: 'Pakistan' }
	];

	const businessHours = 'Mon-Fri from 8am to 5pm (PST)';
	const phoneNumber = '+1 800-000-0000';
</script>

<div class="bg-white px-4 py-16 sm:px-6 lg:px-8">
	<div class="mx-auto flex w-full flex-col items-center gap-12 text-center">
		<div class="flex flex-col items-center gap-6">
			<Badge>Our Locations</Badge>
			<h2 class=" text-4xl font-bold text-gray-900">We are WORLDWIDE</h2>
			<p class="mx-auto max-w-2xl text-lg text-gray-600">
				We help our clients from almost every part of the world.
			</p>
		</div>

		<div class="`scale-[1] relative mx-auto aspect-[16/9] w-fit overflow-hidden rounded-lg">
			<WorldMap />
			<div class="absolute inset-0">
				{#each markers as marker, i}
					<div
						class="absolute h-36 w-36 -translate-x-1/2 -translate-y-1/2"
						style="left: {marker.x}px; top: {marker.y}px;"
					>
						<Ripple />
					</div>
				{/each}
			</div>
		</div>
		<div class="mx-auto grid max-w-7xl w-full grid-cols-1 gap-8 text-left md:grid-cols-3">
			{#each locations as location}
				<div class="text-center text-gray-800">
					<h3 class="mb-2 text-xl font-semibold">{location.country}</h3>
					<p class="mb-4 text-gray-600">{location.address}</p>
					<a href="#" class="font-medium text-[#415EC6] hover:text-[#415EC6]"> Find Us </a>
				</div>
			{/each}

			<div class="text-center text-gray-800">
				<h3 class="mb-2 text-xl font-semibold">Whole Earth</h3>
				<p class="mb-4 text-gray-600">{businessHours}</p>
				<a
					href="tel:{phoneNumber.replace(/\D/g, '')}"
					class="text-sm font-medium text-[#415EC6] hover:text-[#415EC6]"
				>
					{phoneNumber}
				</a>
			</div>
		</div>
	</div>
</div>
