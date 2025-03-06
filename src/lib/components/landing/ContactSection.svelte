<script lang="ts">
	import SectionHeading from './SectionHeading.svelte';
	import { Button } from '$lib/components/ui/button';
	import { Input } from '$lib/components/ui/input';
	import { Textarea } from '$lib/components/ui/textarea';
	import { Checkbox } from '$lib/components/ui/checkbox';
	import { Mail, Phone, MapPin } from 'lucide-svelte';

	const contactInfo = [
		{
			icon: Mail,
			title: 'Email',
			description: 'Our friendly team is here to help.',
			linkText: 'hi@cachelogic.tech',
			linkUrl: 'mailto:hi@cachelogic.tech',
			isLink: true
		},
		{
			icon: Phone,
			title: 'Phone',
			description: 'Mon-Fri from 8am to 5pm.',
			linkText: '+1 (555) 000-0000',
			linkUrl: 'tel:+15550000000',
			isLink: true
		},
		{
			icon: MapPin,
			title: 'Office',
			description: 'Come say hello at our office HQ.',
			linkText: 'Building X, Street Y, Baltimore MD',
			linkUrl: '',
			isLink: false
		}
	];
</script>

<div class="bg-white px-4 py-16 sm:px-6 lg:px-8">
	<div class="mx-auto w-full max-w-7xl">
		<SectionHeading
			badgeText="Contact Us"
			heading="Let's Build the Next Product Together"
			paragraph="We'd love to hear from you. Please fill out this form or shoot us an email."
			align="left"
		/>

		<div class="mt-12 flex w-full flex-col gap-10 lg:flex-row">
			<!-- Contact Info - Left Column -->
			<div class="flex h-fit flex-1 flex-col flex-wrap items-start justify-start gap-8 md:flex-row">
				{#each contactInfo as info}
					<div class="flex h-36 items-start space-x-4">
						<div
							class="flex h-10 w-10 items-center justify-center rounded-full bg-blue-50 text-blue-600"
						>
							<svelte:component this={info.icon} size={20} />
						</div>
						<div>
							<h3 class="text-lg font-medium text-gray-900">{info.title}</h3>
							<p class="mt-1 text-gray-600">{info.description}</p>
							{#if info.isLink}
								<a href={info.linkUrl} class="mt-2 block text-blue-600 hover:underline">
									{info.linkText}
								</a>
							{:else}
								<p class="mt-2 text-blue-600">{info.linkText}</p>
							{/if}
						</div>
					</div>
				{/each}
			</div>

			<!-- Contact Form - Right Column -->
			<div class="flex-1 bg-[#F9FAFB] px-9 py-10">
				<form class="grid grid-cols-1 gap-6 sm:grid-cols-2">
					<div class="space-y-2">
						<label for="first-name" class="text-sm font-medium text-gray-700">First name</label>
						<Input id="first-name" type="text" placeholder="First name" class="w-full rounded-md" />
					</div>

					<div class="space-y-2">
						<label for="last-name" class="text-sm font-medium text-gray-700">Last name</label>
						<Input id="last-name" type="text" placeholder="Last name" class="w-full rounded-md" />
					</div>

					<div class="space-y-2 sm:col-span-2">
						<label for="email" class="text-sm font-medium text-gray-700">Email</label>
						<Input
							id="email"
							type="email"
							placeholder="you@company.com"
							class="w-full rounded-md"
						/>
					</div>

					<div class="space-y-2 sm:col-span-2">
						<label for="message" class="text-sm font-medium text-gray-700">Message</label>
						<Textarea
							id="message"
							placeholder="Leave us a message..."
							class="h-32 w-full rounded-md"
						/>
					</div>

					<div class="flex items-center space-x-2 sm:col-span-2">
						<Checkbox id="privacy-policy" />
						<label for="privacy-policy" class="text-sm text-gray-600">
							You agree to our friendly privacy policy.
						</label>
					</div>

					<div class="sm:col-span-2">
						<Button class="w-full bg-[#1E335F] hover:bg-[#2d4a7f]">Send message</Button>
					</div>
				</form>
			</div>
		</div>
	</div>
</div>
