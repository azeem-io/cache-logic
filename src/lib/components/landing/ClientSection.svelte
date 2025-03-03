<script>
	import GoogleSvg from '$lib/imgs/Google.svg';
	import GitHubSvg from '$lib/imgs/GitHub.svg';
	import UberSvg from '$lib/imgs/Uber.svg';
	import MicrosoftSvg from '$lib/imgs/Microsoft.svg';
	import NotionSvg from '$lib/imgs/Notion.svg';
	import Company1 from '../icons/Company1.svelte';
	import Company2 from '../icons/Company2.svelte';
	import Company3 from '../icons/Company3.svelte';
	import Company4 from '../icons/Company4.svelte';
	import Company5 from '../icons/Company5.svelte';
	import Company6 from '../icons/Company6.svelte';
	import Marquee from '../magic/marquee/Marquee.svelte';
</script>

<section id="clients" class="mx-auto px-6 text-center md:px-8">
	<div class="py-14">
		<div class="max-w-screen mx-auto px-4 md:px-8">
			<h2 class="pb-4 text-center font-medium text-gray-600">
				Join 400+ companies that trust our innovative IT solutions to drive growth and success.
			</h2>
			<Marquee>
				<Company1 />
				<Company2 />
				<Company3 />
				<Company4 />
				<Company5 />
				<Company6 />
			</Marquee>
		</div>
	</div>
</section>
