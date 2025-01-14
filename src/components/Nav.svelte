<script>
	import { page } from '$app/stores';
	let isMobileMenuOpen = false;
</script>

<!-- Google Font -->
<svelte:head>
	<link
		href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600&display=swap"
		rel="stylesheet"
	/>
</svelte:head>

<nav class="sticky top-0 z-50 w-full overflow-hidden bg-gray-50 font-[Poppins]">
	<div class="px-6">
		<div class="flex h-14 justify-between items-center">
			<!-- Logo -->
			<div class="flex items-center">
				<a href="/" class="flex-shrink-0">
					<img class="h-24 w-auto" src="/src/lib/assets/logo-[2]-C.png" alt="Ruthful Notes" />
				</a>
			</div>

			<!-- Main Navigation -->
			<div class="hidden items-center space-x-8 md:flex">
				<a
					href="/"
					class="px-3 py-2 text-sm font-medium text-gray-700 transition-colors duration-200 hover:text-black {
						$page.url.pathname === '/' ? 'font-semibold' : ''
					}"
				>
					Home
				</a>
				<a
					href="/shop"
					class="px-3 py-2 text-sm font-medium text-gray-700 transition-colors duration-200 hover:text-black {
						$page.url.pathname === '/shop' ? 'font-semibold' : ''
					}"
				>
					Shop
				</a>
				<a
					href="/about-us"
					class="px-3 py-2 text-sm font-medium text-gray-700 transition-colors duration-200 hover:text-black {
						$page.url.pathname === '/about-us' ? 'font-semibold' : ''
					}"
				>
					About Us
				</a>
				<a
					href="/contact"
					class="px-3 py-2 text-sm font-medium text-gray-700 transition-colors duration-200 hover:text-black {
						$page.url.pathname === '/contact' ? 'font-semibold' : ''
					}"
				>
					Contact
				</a>
			</div>

			<!-- Search and Login -->
			<div class="hidden items-center space-x-4 md:flex">
				<button class="text-gray-700 hover:text-black">
					<svg
						xmlns="http://www.w3.org/2000/svg"
						class="h-5 w-5"
						fill="none"
						viewBox="0 0 24 24"
						stroke="currentColor"
					>
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"
						/>
					</svg>
				</button>
				<a href="/login" class="text-sm font-medium text-gray-700 hover:text-black">
					Login / Register
				</a>
			</div>

			<!-- Mobile menu button -->
			<div class="flex items-center md:hidden">
				<button
					type="button"
					class="p-2 text-gray-700 hover:text-black"
					on:click={() => (isMobileMenuOpen = !isMobileMenuOpen)}
				>
					<span class="sr-only">Open main menu</span>
					<svg
						class="h-6 w-6"
						xmlns="http://www.w3.org/2000/svg"
						fill="none"
						viewBox="0 0 24 24"
						stroke="currentColor"
					>
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M4 6h16M4 12h16M4 18h16"
						/>
					</svg>
				</button>
			</div>
		</div>
	</div>

	<!-- Mobile menu -->
	{#if isMobileMenuOpen}
		<div class="md:hidden">
			<div class="space-y-1 px-2 pb-3 pt-2">
				<a href="/" class="block px-3 py-2 text-base font-medium text-gray-700 hover:text-black">
					Home
				</a>
				<a href="/shop" class="block px-3 py-2 text-base font-medium text-gray-700 hover:text-black">
					Shop
				</a>
				<a
					href="/about-us"
					class="block px-3 py-2 text-base font-medium text-gray-700 hover:text-black"
				>
					About Us
				</a>
				<a
					href="/contact"
					class="block px-3 py-2 text-base font-medium text-gray-700 hover:text-black"
				>
					Contact
				</a>
				<a href="/login" class="block px-3 py-2 text-base font-medium text-gray-700 hover:text-black">
					Login / Register
				</a>
			</div>
		</div>
	{/if}
</nav>
