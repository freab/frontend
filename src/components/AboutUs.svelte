<script>
	import { onMount } from 'svelte';

	/**
	 * @type {IntersectionObserver}
	 */
	let observer;
	let stats = [
		{ value: 10000, label: 'Lives Impacted', prefix: '+' },
		{ value: 50, label: 'Active Projects', prefix: '' },
		{ value: 100000, label: 'Donations Raised', prefix: '$' }
	];

	$effect(() => {
		observer = new IntersectionObserver(
			(entries) => {
				entries.forEach((entry) => {
					if (entry.isIntersecting) {
						entry.target.classList.add('animate-in');
					}
				});
			},
			{ threshold: 0.2 }
		);

		document.querySelectorAll('.reveal').forEach((el) => observer.observe(el));

		return () => observer.disconnect();
	});
</script>

<div class="overflow-hidden">
	<!-- Hero Section -->
	<section class="relative min-h-[80vh] bg-gray-50">
		<div class="container mx-auto grid min-h-[80vh] px-4 md:grid-cols-2">
			<div class="flex items-center">
				<div class="reveal space-y-6 py-24">
					<span class="text-sm font-medium uppercase tracking-wider text-gray-500">Our Mission</span
					>
					<h1 class="font-satoshi text-5xl font-black leading-tight md:text-6xl">
						Changing Lives,<br />One Person at a Time
					</h1>
					<p class="max-w-lg text-lg text-gray-600">
						At Ruthful Hearts, we believe in the power of individual impact. Every story matters,
						every life counts, and together we're creating lasting change in communities worldwide.
					</p>
					<button
						class="rounded-lg bg-gray-900 px-8 py-4 font-semibold text-white transition-all duration-300 hover:-translate-y-0.5"
						>Join Our Cause</button
					>
				</div>
			</div>
			<div class="relative hidden md:block">
				<!-- <div class="absolute inset-0 z-0 bg-gradient-to-r from-gray-50 to-transparent"></div> -->
				<img src="/src/lib/assets/1.jpg" alt="Impact" class="h-full w-full object-cover" />
			</div>
		</div>
	</section>

	<!-- Story Section -->
	<section class="py-24">
		<div class="container mx-auto px-4">
			<div class="mx-auto max-w-3xl text-center">
				<span class="text-sm font-medium uppercase tracking-wider text-gray-500">Our Story</span>
				<h2 class="font-satoshi mt-3 text-4xl font-bold">Building a Legacy of Hope</h2>
				<p class="mt-6 text-lg text-gray-600">
					What started as a simple act of kindness has grown into a movement. Ruthful Hearts was
					founded on the belief that meaningful change happens one person at a time. Through
					dedicated outreach, community programs, and the support of generous donors, we've
					transformed countless lives.
				</p>
			</div>
		</div>
	</section>

	<!-- Impact Stats -->
	<section class="bg-gray-50 py-24">
		<div class="container mx-auto px-4">
			<div class="grid gap-8 md:grid-cols-3">
				{#each stats as stat}
					<div class="reveal group text-center">
						<div
							class="font-satoshi text-5xl font-black transition-all duration-500 group-hover:scale-110"
						>
							{stat.prefix}{stat.value.toLocaleString()}
						</div>
						<div class="mt-2 text-gray-600">{stat.label}</div>
					</div>
				{/each}
			</div>
		</div>
	</section>

	<!-- Values Section -->
	<section class="py-24">
		<div class="container mx-auto px-4">
			<div class="grid gap-12 md:grid-cols-3">
				<div class="reveal space-y-4">
					<div class="h-16 w-16 rounded-2xl bg-gray-100 p-4">
						<svg class="h-8 w-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								stroke-width="2"
								d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z"
							/>
						</svg>
					</div>
					<h3 class="font-satoshi text-xl font-bold">Compassion First</h3>
					<p class="text-gray-600">
						We lead with empathy and understanding, ensuring every interaction makes a positive
						difference.
					</p>
				</div>
				<div class="reveal space-y-4">
					<div class="h-16 w-16 rounded-2xl bg-gray-100 p-4">
						<svg class="h-8 w-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								stroke-width="2"
								d="M12 4.354a4 4 0 110 5.292M15 21H3v-1a6 6 0 0112 0v1zm0 0h6v-1a6 6 0 00-9-5.197M13 7a4 4 0 11-8 0 4 4 0 018 0z"
							/>
						</svg>
					</div>
					<h3 class="font-satoshi text-xl font-bold">Community Focus</h3>
					<p class="text-gray-600">
						Building stronger communities through sustainable programs and local partnerships.
					</p>
				</div>
				<div class="reveal space-y-4">
					<div class="h-16 w-16 rounded-2xl bg-gray-100 p-4">
						<svg class="h-8 w-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								stroke-width="2"
								d="M13 10V3L4 14h7v7l9-11h-7z"
							/>
						</svg>
					</div>
					<h3 class="font-satoshi text-xl font-bold">Lasting Impact</h3>
					<p class="text-gray-600">
						Creating sustainable change through education, empowerment, and continuous support.
					</p>
				</div>
			</div>
		</div>
	</section>
</div>

<style>
	.reveal {
		opacity: 0;
		transform: translateY(20px);
		transition: all 0.6s ease-out;
	}

	.animate-in {
		opacity: 1;
		transform: translateY(0);
	}
</style>
