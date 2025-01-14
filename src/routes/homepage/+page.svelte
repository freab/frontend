<!-- src/routes/homepage/+page.svelte -->
<script>
	import Experience from './../../components/Experience.svelte';
	import CTA from './../../components/CTA.svelte';
	import Nav from '../../components/Nav.svelte';
	import Featured from '../../components/Featured.svelte';
	import Footer from '../../components/Footer.svelte';
</script>

<Nav />
<CTA />
<Experience />
<Featured />

<!-- <div class="flex h-full w-full flex-col items-center justify-center">
	<span class="pb-4">THIS IS HOMEPAGE</span>
	<a href="/" class="p-2 hover:bg-black hover:text-white"> GO BACK </a>
</div> -->
<Footer />
