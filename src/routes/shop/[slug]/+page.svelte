<script lang="ts">
  import { onMount } from 'svelte';
  import Nav from '../../../components/Nav.svelte';
  import Footer from '../../../components/Footer.svelte';
  import Breadcrumb from '../../../components/Breadcrumb.svelte';
  import img1 from '$lib/assets/1.jpg';
  import img2 from '$lib/assets/2.jpg';
  import img3 from '$lib/assets/3.jpg';
  import img4 from '$lib/assets/4.jpg';
  import { page } from '$app/stores';

  export let data;

  let product = {
    name: 'Rose store',
    category: 'women’s white t-shirt',
    price: 500,
    description: 'Lorem Ipsum has been the industry\'s standard dummy text ever since the 1500s, when an unknown printer took a galley..',
    colors: ['White', 'Gray', 'Black'],
    sizes: ['XS', 'S', 'M', 'L'],
    images: [img1, img2, img3, img4],
  };

  let selectedSize = 'M';
  let selectedColor = 'White';
  let currentTab = 'Description';
  let mainImage = product.images[0];

  let relatedProducts = [
    { name: 'Casual Shirt', price: 400, image: img2 },
    { name: 'Summer Dress', price: 600, image: img3 },
    { name: 'Elegant Blouse', price: 550, image: img4 },
    { name: 'Casual Shirt', price: 400, image: img2 },
  ];

  let quantity = 1;

  let path = `/shop/${$page.params.slug}`;

  function incrementQuantity() {
    quantity = Math.min(quantity + 1, 10); // Limit to 10 items
  }

  function decrementQuantity() {
    quantity = Math.max(quantity - 1, 1); // Minimum 1 item
  }

  function addToCart() {
    // TODO: Implement actual cart functionality
    console.log(`Adding ${quantity} ${product.name} to cart`);
    // You might want to dispatch an event or call a store/service method here
  }
</script>

<div class="min-h-screen bg-white">
  <Nav />
  <Breadcrumb path={path} />
  
  <div class="container mx-auto px-4 py-6 grid grid-cols-1 md:grid-cols-2 gap-16">
    <!-- Left - Product Image -->
    <div class="bg-gray-50 rounded-lg overflow-hidden shadow-sm mb-6">
      <img src={mainImage} alt={product.name} class="w-full h-auto object-cover object-center" />
    </div>

    <!-- Right - Product Details -->
    <div>
      <div class="flex justify-between items-center">
        <div class="">
          <h1 class="text-3xl font-semibold text-gray-900">{product.name}</h1>
          <p class="text-gray-500">{product.category}</p></div>
          <span class="inline-block bg-green-500 text-white text-xs px-4 py-2 rounded-lg">In stock</span>
      </div>
      <p class="text-2xl font-bold text-gray-800 mt-4">ETB {product.price}</p>
      <p class="text-gray-700 text-sm mt-4">{product.description}</p>
      
      <!-- Color Selection -->
      <div class="mt-6">
        <h3 class="text-sm font-medium text-gray-700">Color</h3>
        <div class="flex gap-2 mt-2">
          {#each product.colors as color}
            <button 
              style={`background-color: ${color};borde`}
              class={`w-10 h-10 p-3 rounded-md m-0 ${selectedColor === color ? 'border-2 border-gray-500' : 'border-2 border-gray-300'}`} 
              on:click={() => selectedColor = color}
              on:keydown={(e) => {
                if (e.key === 'Enter' || e.key === ' ') {
                  selectedColor = color;
                }
              }}
              class:border-gray-600={selectedColor === color}
              class:bg-black={selectedColor === color} 
              class:text-white={selectedColor === color}  
              class:border-black={selectedColor === color}
            >
            </button>
          {/each}
        </div>
      </div>

      <!-- Size Selection -->
      <div class="mt-6">
        <h3 class="text-sm font-medium text-gray-700">Size</h3>
        <div class="flex gap-1 mt-2">
          {#each product.sizes as size}
            <button class="px-4 py-2 border rounded-md text-sm transition-all duration-200"
                    class:bg-black={selectedSize === size} 
                    class:text-white={selectedSize === size}  
                    class:border-black={selectedSize === size}
                    on:click={() => selectedSize = size}>
              {size}
            </button>
          {/each}
        </div>
      </div>

      <!-- Quantity and Actions -->
      <div class="mt-6 flex items-center space-x-4">
        <button 
          class="px-4 py-2 border rounded-md hover:bg-gray-100 transition-colors"
          on:click={decrementQuantity}
          disabled={quantity <= 1}
        >
          -
        </button>
        <span class="text-lg w-8 text-center">{quantity}</span>
        <button 
          class="px-4 py-2 border rounded-md hover:bg-gray-100 transition-colors"
          on:click={incrementQuantity}
          disabled={quantity >= 10}
        >
          +
        </button>
      </div>
      
      <div class="mt-6 flex space-x-4">
        <button 
          class="w-full bg-black text-white py-3 rounded-md hover:bg-gray-900 transition-colors"
          on:click={addToCart}
        >
          Add {quantity} to cart
        </button>
        <button class="p-3 border border-gray-300 rounded-md">
          ❤️
        </button>
      </div>
    </div>
  </div>
  <!-- Other Images-->
   <div class="container mx-auto flex gap-3 px-4 py-4">
   {#each product.images as image}
   <button 
   on:click={() => mainImage = image}
   on:keydown={(e) => {
     if (e.key === 'Enter' || e.key === ' ') {
       mainImage = image;
     }
   }}
   tabindex="0"
   class="focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-gray-500 rounded-lg"
   aria-label="View alternative product image 1"
 >
   <img src={image} alt="" class="bg-gray-600 rounded-lg shadow-xl h-32 w-32 object-cover" />
 </button>
   {/each}

   </div>
   <div class="container mx-auto px-4 py-4">
    <div class="border-b border-gray-200">
      <div class="flex space-x-4">
        <button class="text-lg font-semibold px-2 py-1"
                class:text-black={currentTab === 'Description'}
                class:text-gray-500={currentTab !== 'Description'}
                class:border-b-2={currentTab === 'Description'}
                class:border-black={currentTab === 'Description'}
                on:click={() => currentTab = 'Description'}>
          Description
        </button>
        <button class="text-lg font-semibold px-2 py-1"
                class:text-black={currentTab === 'Additional Information'}
                class:text-gray-500={currentTab !== 'Additional Information'}
                class:border-b-2={currentTab === 'Additional Information'}
                class:border-black={currentTab === 'Additional Information'}
                on:click={() => currentTab = 'Additional Information'}>
          Additional Information
        </button>
      </div>
    </div>
    
    {#if currentTab === 'Description'}
      <p class="text-gray-700 mt-4">{product.description}</p>
    {:else}
      <p class="text-gray-700 mt-4">No additional information available.</p>
    {/if}
  </div>

  <div class="container mx-auto px-4 py-4">
    <h2 class="text-xl font-semibold text-gray-900 mb-4">Related Products</h2>
    <div class="grid grid-cols-1 md:grid-cols-5 gap-4">
      {#each relatedProducts as product}
        <button class="p-2 border rounded-lg shadow-md hover:shadow-lg transition"
                on:click={() => console.log(`Navigating to ${product.name}`)}>
          <img src={product.image} alt={product.name} class="bg-gray-600 rounded-lg shadow-xl h-32 w-full object-cover" />
          <p class="text-sm font-semibold text-gray-900 mt-2">{product.name}</p>
          <p class="text-gray-700 text-sm">ETB {product.price}</p>
        </button>
      {/each}
    </div>
  </div>
  

  <Footer />
</div>

<style>
  button {
    -webkit-tap-highlight-color: transparent;
  }
</style>
