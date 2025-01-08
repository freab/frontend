<!-- src/routes/homepage/+page.svelte -->
<script>
	import Nav from '../../components/Nav.svelte';
	import Scene from '../../components/Scene.svelte';
	import Featured from '../../components/Featured.svelte';
	import Footer from '../../components/Footer.svelte';
	import AboutUs from '../../components/AboutUs.svelte';
</script>

<Nav />
<Scene />
<Featured />
<AboutUs />

<div class="flex h-screen w-screen flex-col items-center justify-center">
	<span class="pb-4">THIS IS HOMEPAGE</span>
	<a href="/" class="p-2 hover:bg-black hover:text-white"> GO BACK </a>
</div>
<Footer />
