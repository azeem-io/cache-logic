<script>
	import { seo } from '$lib';
	import ClientSection from '$lib/components/landing/ClientSection.svelte';
	import HeroSection from '$lib/components/landing/HeroSection.svelte';
	import LocationSection from '$lib/components/landing/LocationSection.svelte';
	import AboutSection from '$lib/components/landing/AboutSection.svelte';
	import ServicesSection from '$lib/components/landing/ServicesSection.svelte';
	import TeamSection from '$lib/components/landing/TeamSection.svelte';
	import ContactSection from '$lib/components/landing/ContactSection.svelte';
	import PortfolioSection from '$lib/components/landing/PortfolioSection.svelte';
	import BackgroundPattern from '$lib/components/svgs/BackgroundPattern.svelte';
</script>

<svelte:head>
	<title>{seo.title}</title>
	<meta name="description" content={seo.description} />
	<meta name="keywords" content={seo.keywords} />

	<meta property="og:title" content={seo.title} />
	<meta property="og:description" content={seo.description} />
	<meta property="og:image" content={seo.image} />
	<meta property="og:site_name" content={seo.title} />
	<meta property="og:url" content={seo.url} />

	<meta name="twitter:card" content="summary_large_image" />
	<meta name="twitter:title" content={seo.title} />
	<meta name="twitter:description" content={seo.description} />
	<meta name="twitter:image" content={seo.image} />
	<meta name="twitter:site" content="@cache_logic" />
</svelte:head>

<BackgroundPattern />
<HeroSection />
<ClientSection />
<ServicesSection />
<PortfolioSection />
<AboutSection />
<TeamSection />
<LocationSection />
<ContactSection />
