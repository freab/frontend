<script>
	import { writable } from 'svelte/store';

	// Sample Featured Products (replace with your actual product data)
	const featuredProducts = writable([
		{
			id: 1,
			name: 'Limited Edition Tee',
			image: '/src/lib/assets/1.jpg',
			price: '500 ETB',
			description: 'A premium cotton tee with a unique design.'
		},
		{
			id: 2,
			name: 'Classic Hoodie',
			image: '/src/lib/assets/2.jpg',
			price: '800 ETB',
			description: 'A comfortable and warm hoodie for everyday wear.'
		},
		{
			id: 3,
			name: 'Embroidered Cap',
			image: '/src/lib/assets/3.jpg',
			price: '300 ETB',
			description: 'A stylish cap with embroidered logo detail.'
		},
		{
			id: 4,
			name: 'Tote Bag',
			image: '/src/lib/assets/4.jpg',
			price: '200 ETB',
			description: 'A spacious tote bag with a unique design.'
		}
	]);
</script>

<section class="featured-products bg-white py-12">
	<div class="container mx-auto px-4">
		<h2 class="mb-8 text-center text-4xl font-bold text-gray-800">Featured Products</h2>

		<div
			class="grid grid-cols-1 gap-8 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 2xl:grid-cols-5"
		>
			{#each $featuredProducts as product}
				<div
					class="product-card relative overflow-hidden rounded-3xl bg-white shadow-md transition-transform duration-300 hover:scale-105 hover:shadow-lg"
				>
					<img
						src={product.image}
						alt={product.name}
						class="h-64 w-full rounded-t-3xl object-cover"
					/>
					<div class="p-6">
						<h3 class="mb-2 text-xl font-semibold text-gray-900">{product.name}</h3>
						<p class="mb-4 text-sm text-gray-600">{product.description}</p>
						<div class="flex items-center justify-between">
							<span class="text-lg font-bold text-gray-800">{product.price}</span>
							<button
								class="rounded-full bg-pink-500 px-4 py-2 font-bold text-white transition-colors duration-300 hover:bg-pink-700"
							>
								Buy
							</button>
						</div>
					</div>
				</div>
			{/each}
		</div>

		<div class="mt-8 text-center">
			<a
				href="/shop"
				class="rounded-lg bg-gray-800 px-6 py-3 font-bold text-white transition-colors duration-300 hover:bg-gray-900"
			>
				View All Products
			</a>
		</div>
	</div>
</section>

<style>
	/* Optional: Add custom styles for product cards and other elements */
	.product-card {
		transition: transform 0.2s;
	}

	.product-card:hover {
		transform: scale(1.02);
		box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
	}
</style>
