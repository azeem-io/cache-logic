<script lang="ts">
	import Ripple from '../magic/Ripple.svelte';
	import Badge from '../magic/Badge.svelte';
	import SectionHeading from './SectionHeading.svelte';
	import { ArrowUpRightIcon } from 'lucide-svelte';
	import Button from '$lib/components/ui/button/button.svelte';
	import TwitterIcon from '../svgs/TwitterIcon.svelte';
	import LinkedinIcon from '../svgs/LinkedinIcon.svelte';
	import DribbleIcon from '../svgs/DribbleIcon.svelte';

	const teamMembers = [
		{
			id: 'faizan',
			name: 'Faizan Ahmad',
			role: 'Founder & CEO',
			bio: 'Former co-founder of Opendoor. Early staff at Apple and Google.',
			image: '/images/team1.png',
			featured: true,
			socials: [
				{ icon: TwitterIcon, url: '#' },
				{ icon: LinkedinIcon, url: '#' },
				{ icon: DribbleIcon, url: '#' }
			]
		},
		{
			id: 'abdullah',
			name: 'Abdullah Sarfaraz',
			role: 'Co-Founder',
			bio: '',
			image: '/images/team2.png',
			featured: false,
			socials: []
		},
		{
			id: 'annie',
			name: 'Annie Stanley',
			role: 'Product Manager',
			bio: '',
			image: '/images/team3.png',
			featured: false,
			socials: []
		}
	];
</script>

<div class="bg-white px-4 py-16 sm:px-6 lg:px-8">
	<div class="mx-auto flex w-full flex-col items-center gap-12 text-center">
		<SectionHeading
			badgeText="Our Team"
			heading="Meet Our Team"
			paragraph="Our philosophy is simple — hire a team of diverse, passionate people and foster a
				culture that empowers you to do your best work."
		/>

		<div class="flex w-full justify-center flex-row gap-4">
			<Button class="w-full md:w-fit" href="#" variant="outline">Read our principles</Button>
			<Button class="w-full md:w-fit" href="#">We're hiring!</Button>
		</div>

		<div class="mx-auto flex w-full max-w-5xl flex-col gap-6 lg:flex-row">
			<div
				class="relative aspect-[4/3] min-h-[30rem] w-full overflow-hidden rounded-t-3xl shadow-[0px_8px_32px_rgba(29,57,102,0.6)] lg:w-3/5 lg:rounded-l-3xl lg:rounded-tr-none"
				style=""
			>
				<img
					src={teamMembers[0].image}
					alt={teamMembers[0].name}
					class="h-full w-full object-cover"
				/>
				<div class="absolute bottom-0 left-0 right-0 p-4 text-left text-white lg:p-6">
					<button
						class="w-full rounded-2xl border border-white/30 bg-white/10 px-5 py-6 text-left backdrop-blur-md"
					>
						<div class="flex flex-col font-semibold">
							<h3 class="flex w-full justify-between text-3xl">
								{teamMembers[0].name}
								<ArrowUpRightIcon />
							</h3>
							<p class="text-lg">{teamMembers[0].role}</p>
							<p class="mt-1">{teamMembers[0].bio}</p>
						</div>
						<div class="mt-4 hidden space-x-3 md:flex">
							{#each teamMembers[0].socials as social}
								<a href={social.url} class="text-white hover:text-gray-300">
									<svelte:component this={social.icon} />
								</a>
							{/each}
						</div>
					</button>
				</div>
			</div>

			<!-- Other team members -->
			<div class="flex w-full flex-col gap-6 lg:w-2/5">
				{#each teamMembers.slice(1) as member, i}
					<div
						class="relative w-full flex-1 overflow-hidden shadow-[0px_8px_32px_rgba(29,57,102,0.6)] {i ==
						0
							? 'lg:rounded-tr-3xl'
							: 'rounded-b-3xl rounded-bl-none lg:rounded-br-3xl'}"
						style="aspect-ratio: 8/7;"
					>
						<img src={member.image} alt={member.name} class="h-full w-full object-cover" />
						<div class="absolute bottom-0 left-0 right-0 p-4 text-left text-white lg:p-6">
							<button
								class="w-full rounded-2xl border border-white/30 bg-white/10 px-5 py-6 text-left backdrop-blur-md"
							>
								<div class="flex flex-col gap-4 font-semibold">
									<h3 class="flex w-full justify-between text-3xl">
										{member.name}
										<ArrowUpRightIcon />
									</h3>
									<p class="text-lg text-gray-200">{member.role}</p>
								</div>
							</button>
						</div>
					</div>
				{/each}
			</div>
		</div>
	</div>
</div>
