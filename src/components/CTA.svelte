<script>
	import bigshirt from '$lib/assets/2.jpg'
	
</script>

<div class="relative overflow-hidden w-full h-full bg-gray-50">
    <div class="absolute inset-0 bg-gray-50/50"></div>
    <div class="container relative w-full h-full mx-auto">
        <div class="grid items-center gap-16 md:grid-cols-2 w-full h-full">
            <div class="space-y-8">
				<div class="flex items-center space-x-2">
					<span class="inline-block w-8 h-0.5 bg-gray-400"/>
					<span class="text-sm font-medium uppercase tracking-wider text-gray-500">
					  RuthfulHeart Merch Store
					</span>
				  </div>
	  
				  <h2 class="font-satoshi text-5xl font-black md:text-7xl leading-tight">
					<span class="block">Shop or Browse</span>
					<span class=" top-1 block bg-clip-text text-transparent bg-gradient-to-r from-purple-600 to-blue-600">
					  Authentic Merch
					</span>
				  </h2>
	  
				  <p class="text-xl leading-relaxed text-gray-600 max-w-lg">
					Every purchase from our store directly supports our mission. Join us in making 
					a difference, one person at a time.
				  </p>
                <div class="flex gap-4">
                    <a href="/shop" class="rounded-xl bg-black px-8 py-4 font-semibold text-white shadow-lg transition-all duration-300 hover:-translate-y-0.5 hover:shadow-xl">
                        Start Shopping
                    </a>
                    <a href="/donate" class="rounded-xl border-2 border-black px-8 py-4 font-semibold text-black transition-all duration-300 hover:-translate-y-0.5 hover:bg-black hover:text-white">
                        Donate
                    </a>
                </div>
            </div>
            <div class="relative aspect-[5/5] overflow-hidden rounded-3xl bg-white shadow-2xl w-full h-full">
                <img src={bigshirt} alt="Merchandise Display" class="h-full w-full object-cover transition-transform duration-700 hover:scale-105"/>
            </div>
        </div>
    </div>
</div>
