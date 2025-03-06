<script>
	import Company1 from '../svgs/Company1.svelte';
	import Company2 from '../svgs/Company2.svelte';
	import Company3 from '../svgs/Company3.svelte';
	import Company4 from '../svgs/Company4.svelte';
	import Company5 from '../svgs/Company5.svelte';
	import Company6 from '../svgs/Company6.svelte';
	import Marquee from '../magic/marquee/Marquee.svelte';
</script>

<section id="clients" class="mx-auto mt-20 px-4 text-center md:mt-0 md:px-8">
	<div class="md:py-14">
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
