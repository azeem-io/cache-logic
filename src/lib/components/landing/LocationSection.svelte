<script lang="ts">
	import { AnimatePresence, Motion, useMotionValue, useSpring, useTransform } from 'svelte-motion';
	import Ripple from '../magic/Ripple.svelte';
	import WorldMap from './WorldMap.svelte';
	import Badge from '../magic/Badge.svelte';
	import * as Tooltip from '$lib/components/ui/tooltip';
	import SectionHeading from './SectionHeading.svelte';

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
		{ id: 'us', x: 17, y: 45, label: 'United States' },
		{ id: 'pk', x: 66, y: 49, label: 'Pakistan' }
	];

	const businessHours = 'Mon-Fri from 8am to 5pm (PST)';
	const phoneNumber = '+1 800-000-0000';
</script>

<div class="bg-white px-4 py-8 sm:px-6 md:py-16 lg:px-8">
	<div class="mx-auto flex w-full flex-col items-center gap-12 text-center">
		<SectionHeading
			badgeText="Our Locations"
			heading="We are WORLDWIDE"
			paragraph="We help our clients from almost every part of the world."
		/>
		<div
			class="`scale-[1] relative mx-auto aspect-[16/9] w-full max-w-5xl overflow-hidden rounded-lg"
		>
			<WorldMap />
			<div class="absolute inset-0">
				{#each markers as marker, i}
					<div
						class="absolute h-36 w-36 -translate-x-1/2 -translate-y-1/2"
						style="left: {marker.x}%; top: {marker.y}%;"
					>
						<Ripple />
					</div>
				{/each}
			</div>
		</div>
		<div class="mx-auto grid w-full max-w-7xl grid-cols-1 gap-8 text-left md:grid-cols-3">
			{#each locations as location}
				<div class="text-center text-gray-800">
					<h3 class="mb-2 text-xl font-semibold">{location.country}</h3>
					<p class="mb-4 text-gray-600">{location.address}</p>
					<a href="#" class="font-semibold text-[#415EC6] hover:text-[#415EC6]"> Find Us </a>
				</div>
			{/each}

			<div class="text-center text-gray-800">
				<h3 class="mb-2 text-xl font-semibold">Whole Earth</h3>
				<p class="mb-4 text-gray-600">{businessHours}</p>
				<a
					href="tel:{phoneNumber.replace(/\D/g, '')}"
					class="text-sm font-semibold text-[#415EC6] hover:text-[#415EC6]"
				>
					{phoneNumber}
				</a>
			</div>
		</div>
	</div>
</div>
