<script>
	import WorldMap from './WorldMap.svelte';

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
	<div class="mx-auto w-full text-center">
		<button
			class="mb-4 rounded-full bg-gray-100 px-4 py-2 text-sm font-medium text-[#57C5FF] transition-colors hover:bg-gray-200"
		>
			Our Locations
		</button>

		<h2 class="mb-4 text-4xl font-bold text-gray-900">We are WORLDWIDE</h2>
		<p class="mx-auto mb-12 max-w-2xl text-lg text-gray-600">
			We help our clients from almost every part of the world.
		</p>

		<div class="relative mx-auto aspect-[16/9] w-fit overflow-hidden rounded-lg">
			<WorldMap />
			<div class="absolute inset-0">
				{#each markers as marker}
					<div
						class="absolute h-3 w-3 -translate-x-1/2 -translate-y-1/2 rounded-full bg-[#57C5FF]"
						style="left: {marker.x}px; top: {marker.y}px;"
					>
						<span
							class="absolute hidden -translate-x-1/2 -translate-y-full whitespace-nowrap rounded bg-gray-800 px-2 py-1 text-xs text-white"
							style="left: 50%; top: -24px;"
						>
							{marker.label}
						</span>
					</div>
				{/each}
			</div>
		</div>

		<div class="mx-auto grid max-w-4xl grid-cols-1 gap-8 text-left md:grid-cols-3">
			{#each locations as location}
				<div class="text-gray-800">
					<h3 class="mb-2 text-xl font-semibold">{location.country}</h3>
					<p class="mb-4 text-gray-600">{location.address}</p>
					<a href="#" class="text-sm font-medium text-[#57C5FF] hover:text-[#46B0F0]"> Find Us </a>
				</div>
			{/each}

			<div class="text-gray-800">
				<h3 class="mb-2 text-xl font-semibold">Whole Earth</h3>
				<p class="mb-4 text-gray-600">{businessHours}</p>
				<a
					href="tel:{phoneNumber.replace(/\D/g, '')}"
					class="text-sm font-medium text-[#57C5FF] hover:text-[#46B0F0]"
				>
					{phoneNumber}
				</a>
			</div>
		</div>
	</div>
</div>
