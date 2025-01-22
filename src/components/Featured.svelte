<script>
	import asset1 from '$lib/assets/1.jpg';
	import asset2 from '$lib/assets/2.jpg';
	import asset3 from '$lib/assets/3.jpg';
	import asset4 from '$lib/assets/4.jpg';

	export let products = [
		{ id: 1, name: 'T-Shirt', price: '$49.00', img: asset1 },
		{ id: 2, name: 'T-Shirt', price: '$29.00', img: asset2 },
		{ id: 3, name: 'T-Shirt', price: '$70.00', img: asset3 },
		{ id: 4, name: 'T-Shirt', price: '$59.00', img: asset4 }
	];
</script>

<div class="bg-gray-50/50 py-12 text-black">
	<!-- Hero Section -->
	<div
		class="relative bg-cover bg-center py-20 text-center after:absolute after:inset-0"
		style="background-image: url('{asset1}');"
	>
		<h1 class="relative z-10 text-5xl font-extrabold leading-tight tracking-wide text-white">
			The Trends for the Season
		</h1>
		<p class="relative z-10 mt-6 text-xl text-white">Unique T-Shirt</p>
	</div>

	<!-- Product Grid -->
	<div class="grid grid-cols-1 gap-12 p-12 sm:grid-cols-2 lg:grid-cols-4">
		{#each products as product (product.id)}
			<div
				class="transform overflow-hidden rounded-lg border-2 border-black transition-all duration-500 hover:scale-105 hover:shadow-[0_0_20px_rgba(0,0,0,0.8)]"
			>
				<img src={product.img} alt={product.name} class="h-56 w-full object-cover" />
				<div class="p-6 text-center">
					<h3 class="text-xl font-semibold">{product.name}</h3>
					<p class="mt-2 text-gray-600">{product.price}</p>
					<button
						class="mt-6 rounded-full border-2 border-black px-6 py-2 text-black transition-all duration-300 hover:bg-black hover:text-white"
					>
						Add to Cart
					</button>
				</div>
			</div>
		{/each}
	</div>

	<!-- Button Container -->
	<div class="mt-16 text-center space-x-4">
		<button
			class="rounded-full border-2 border-black px-8 py-3 text-black transition-all duration-300 hover:bg-black hover:text-white"
		>
		<a href="/experience">
			Customize Your Own Hoodie
		</a>
		</button>
		<button
			class="rounded-full border-2 border-black px-8 py-3 text-black transition-all duration-300 hover:bg-black hover:text-white"
		>
			
			<a href="/shop">
				View All Products
			</a>
		</button>
	</div>
</div>