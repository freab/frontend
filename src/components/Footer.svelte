<script>
	import  logo from '$lib/assets/logo-[2]-C.png';
    import noise from '$lib/assets/noise.png'
    import { base } from '$app/paths';
</script>

<svelte:head>
    <link
        href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap"
        rel="stylesheet"
    />
</svelte:head>

<footer class="font-poppins py-16 bg-gray-50 relative overflow-hidden">
    <!-- Noise Texture Background -->
    <div class="absolute inset-0 bg-[url({noise})] opacity-10 pointer-events-none"></div>

    <div class="container mx-auto px-4 relative z-10">
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-12">
            <!-- Logo & Description -->
            <div class="space-y-6">
                <img
                    src="{logo}"
                    alt="Ruthful Hearts Logo"
                    class="h-24 transition-all duration-300 hover:opacity-90"
                />
                <p class="text-sm leading-relaxed text-gray-600">
                    Transforming lives one person at a time, with your help.
                </p>
            </div>

            <!-- Navigation Links - First Column -->
            <div>
                <h3 class="mb-5 text-sm font-bold uppercase tracking-wider text-gray-500">
                    Explore
                </h3>
                <nav class="flex flex-col space-y-3">
                    <a
                        href="/about-us"
                        class="text-base transition-all duration-300 hover:-translate-y-0.5 hover:text-gray-900"
                        >About Us</a
                    >
                    <a
                        href="/about-us"
                        class="text-base transition-all duration-300 hover:-translate-y-0.5 hover:text-gray-900"
                        >Our Story</a
                    >
                    <a
                        href="/cart"
                        class="text-base transition-all duration-300 hover:-translate-y-0.5 hover:text-gray-900"
                        >Cart</a
                    >
                    <a
                        href="/shop"
                        class="text-base transition-all duration-300 hover:-translate-y-0.5 hover:text-gray-900"
                        >Shop</a
                    >
                </nav>
            </div>

            <!-- Navigation Links - Second Column -->
            <div>
                <h3 class="mb-5 text-sm font-bold uppercase tracking-wider text-gray-500">
                    Connect
                </h3>
                <nav class="flex flex-col space-y-3">
                    <a
                        href="/contact"
                        class="text-base transition-all duration-300 hover:-translate-y-0.5 hover:text-gray-900"
                        >Get in Touch</a
                    >
                    <a
                        href="/support"
                        class="text-base transition-all duration-300 hover:-translate-y-0.5 hover:text-gray-900"
                        >Support</a
                    >
                    <a
                        href="/faq"
                        class="text-base transition-all duration-300 hover:-translate-y-0.5 hover:text-gray-900"
                        >FAQ</a
                    >
                    <a
                        href="/blog"
                        class="text-base transition-all duration-300 hover:-translate-y-0.5 hover:text-gray-900"
                        >Blog</a
                    >
                </nav>
            </div>

            <!-- Social Media & Newsletter -->
            <div class="space-y-6">
                <div class="flex space-x-5">
                    <a
                        href="#"
                        class="group rounded-full bg-gray-100 p-3 transition-all duration-300 hover:-translate-y-1 hover:bg-gray-200"
                    >
                        <svg
                            class="h-5 w-5 text-gray-600 transition-colors group-hover:text-gray-900"
                            fill="currentColor"
                            viewBox="0 0 24 24"
                        >
                            <path
                                d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"
                            />
                        </svg>
                    </a>
                    <a
                        href="#"
                        class="group rounded-full bg-gray-100 p-3 transition-all duration-300 hover:-translate-y-1 hover:bg-gray-200"
                    >
                        <svg
                            class="h-5 w-5 text-gray-600 transition-colors group-hover:text-gray-900"
                            fill="currentColor"
                            viewBox="0 0 24 24"
                        >
                            <path
                                d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.061a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.937 4.937 0 004.604 3.417 9.868 9.868 0 01-6.102 2.105c-.39 0-.779-.023-1.17-.067a13.995 13.995 0 007.557 2.209c9.054 0 13.999-7.496 13.999-13.986 0-.209 0-.42-.015-.63a9.936 9.936 0 002.46-2.548l-.047-.02z"
                            />
                        </svg>
                    </a>
                    <a
                        href="#"
                        class="group rounded-full bg-gray-100 p-3 transition-all duration-300 hover:-translate-y-1 hover:bg-gray-200"
                    >
                        <svg
                            class="h-5 w-5 text-gray-600 transition-colors group-hover:text-gray-900"
                            fill="currentColor"
                            viewBox="0 0 24 24"
                        >
                            <path
                                d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"
                            />
                        </svg>
                    </a>
                </div>
                <div class="space-y-4">
                    <h3 class="text-sm font-bold uppercase tracking-wider text-gray-500">
                        Stay Updated
                    </h3>
                    <div class="flex flex-col md:flex-row gap-2">
                        <input
                            type="email"
                            placeholder="Enter your email"
                            class="w-full rounded-lg border border-gray-300 bg-gray-50 px-4 py-2.5 text-sm transition-all duration-300 placeholder:text-gray-500 focus:border-gray-900 focus:outline-none focus:ring-0"
                        />
                        <button
                            class="rounded-lg bg-gray-900 px-6 py-2.5 text-sm font-semibold text-white transition-all duration-300 hover:-translate-y-0.5 hover:bg-gray-800"
                            >Join</button
                        >
                    </div>
                </div>
            </div>
        </div>
    </div>
</footer>

<style>
    :global(body) {
        font-family: 'Poppins', sans-serif;
    }
</style>