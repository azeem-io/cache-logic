<script lang="ts">
	import Ripple from '../magic/Ripple.svelte';
	import WorldMap from './WorldMap.svelte';
	import Badge from '../magic/Badge.svelte';
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
		{ id: 'us', x: 170, y: 215, label: 'United States' },
		{ id: 'pk', x: 695, y: 230, label: 'Pakistan' }
	];

	const businessHours = 'Mon-Fri from 8am to 5pm (PST)';
	const phoneNumber = '+1 800-000-0000';
</script>

<div class="bg-white px-4 py-16 sm:px-6 lg:px-8">
	<div class="mx-auto flex w-full flex-col items-center gap-12 text-center">
		<SectionHeading
			badgeText="Why Us"
			heading="How does Cache Logic stands out?"
			paragraph="At Cache Logic, we are a passionate team of tech experts dedicated to powering your IT
				evolution. Founded by industry leaders with diverse expertise, we focus on delivering
				innovative, reliable, and scalable tech solutions—from AI and automation to cybersecurity
				and app development. Our mission is simple: help your business stay ahead in a digital
				world."
		/>

		<img
			src="/images/meeting.png"
			alt="meeting"
			class="w-full max-w-5xl rounded-[16px] border border-[4px] border-[#3A6EB3] shadow-xl"
		/>

		<div class="mx-auto grid w-full max-w-7xl grid-cols-1 gap-8 text-left md:grid-cols-3">
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
