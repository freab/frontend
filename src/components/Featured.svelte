<script>
	export let products = [
		{ id: 1, name: 'T-Shirt', price: '$49.00', img: '/src/lib/assets/1.jpg' },
		{ id: 2, name: 'T-Shirt', price: '$29.00', img: '/src/lib/assets/2.jpg' },
		{ id: 3, name: 'T-Shirt', price: '$70.00', img: '/src/lib/assets/3.jpg' },
		{ id: 4, name: 'T-Shirt', price: '$59.00', img: '/src/lib/assets/4.jpg' }
	];
</script>

<div class="bg-white py-12 text-black">
	<div
		class="relative bg-cover bg-center py-20 text-center after:absolute after:inset-0"
		style="background-image: url('/src/lib/assets/1.jpg');"
	>
		<h1 class="relative z-10 text-5xl font-extrabold leading-tight tracking-wide text-white">
			The Trends for the Season
		</h1>
		<p class="relative z-10 mt-6 text-xl text-white">Unique T-Shirt</p>
	</div>

	<div class="grid grid-cols-1 gap-12 p-12 sm:grid-cols-2 lg:grid-cols-4">
		{#each products as product (product.id)}
			<div
				class="transform overflow-hidden rounded-lg bg-gray-100 shadow-2xl transition-all duration-500 hover:scale-105 hover:shadow-[0_0_20px_rgba(0,0,0,0.8)]"
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

	<div class="mt-16 text-center">
		<button
			class="rounded-full border-2 border-black px-8 py-3 text-black transition-all duration-300 hover:bg-black hover:text-white"
		>
			View More
		</button>
	</div>
</div>
