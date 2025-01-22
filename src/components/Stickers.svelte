<script lang="ts">
    import asset1 from '$lib/assets/1.jpg';
    import asset2 from '$lib/assets/2.jpg';
    import asset3 from '$lib/assets/3.jpg';
    import asset4 from '$lib/assets/4.jpg';

    // Duplicate images for a longer scroll effect
    const images: string[] = [asset1, asset2, asset3, asset4, asset1, asset2, asset3, asset4];

    // Generate random prices for each image
    const prices: number[] = images.map(() => Math.floor(Math.random() * 50) + 10);

    // Drag functionality
    let isDragging: boolean = false;
    let startX: number;
    let scrollLeft: number;

    function startDrag(event: MouseEvent) {
        isDragging = true;
        startX = event.pageX;
        const target = event.currentTarget as HTMLElement;
        scrollLeft = target.scrollLeft;
    }

    function stopDrag() {
        isDragging = false;
    }

    function onDrag(event: MouseEvent) {
        if (!isDragging) return;
        event.preventDefault();
        const x = event.pageX - startX;
        const target = event.currentTarget as HTMLElement;
        target.scrollLeft = scrollLeft - x;
    }
</script>

<style>
    .sticker-section {
        background: transparent;
        padding: 2rem 0;
    }

    .sticker-scroll-container {
        overflow-x: auto;
        scroll-behavior: smooth;
        scroll-snap-type: x mandatory;
        -webkit-overflow-scrolling: touch;
        cursor: grab;
    }

    .sticker-scroll-container:active {
        cursor: grabbing;
    }

    .sticker-container {
        display: flex;
        gap: 1.5rem;
        padding: 1.5rem;
    }

    .sticker-item {
        scroll-snap-align: start;
        flex: 0 0 auto;
        width: 250px;
        border-radius: 12px;
        overflow: hidden;
        border: 2px solid black;
        transition: all 0.3s ease;
        background: white;
    }

    .sticker-item:hover {
        transform: scale(1.05);
        box-shadow: 0 0 20px rgba(0, 0, 0, 0.8);
    }

    .sticker-item img {
        width: 100%;
        height: 200px;
        object-fit: cover;
    }

    .sticker-content {
        padding: 1rem;
        text-align: center;
    }

    .sticker-name {
        font-size: 1.25rem;
        font-weight: 600;
        margin-bottom: 0.5rem;
    }

    .sticker-price {
        font-size: 1rem;
        color: #666;
        margin-bottom: 1rem;
    }

    .add-to-cart-button {
        background: transparent;
        border: 2px solid black;
        border-radius: 9999px;
        padding: 0.5rem 1.5rem;
        font-size: 1rem;
        font-weight: 600;
        cursor: pointer;
        transition: all 0.3s ease;
    }

    .add-to-cart-button:hover {
        background: black;
        color: white;
    }

    /* Hide scrollbar */
    .sticker-scroll-container::-webkit-scrollbar {
        display: none;
    }

    .sticker-scroll-container {
        -ms-overflow-style: none; /* IE and Edge */
        scrollbar-width: none; /* Firefox */
    }

    /* Button styles */
    .action-button {
        background: transparent;
        border: 2px solid black;
        border-radius: 9999px;
        padding: 0.75rem 2rem;
        font-size: 1rem;
        font-weight: 600;
        cursor: pointer;
        transition: all 0.3s ease;
        text-align: center;
        width: fit-content;
    }

    .action-button:hover {
        background: black;
        color: white;
    }

    /* Button container */
    .button-container {
        display: flex;
        justify-content: center;
        gap: 1.5rem;
        margin-top: 2rem;
    }
</style>

<section class="sticker-section">
    <h2 class="text-5xl font-extrabold text-center mb-6">Explore Our Sticker Collection</h2>
    <p class="text-xl text-center mb-12">Unique and creative stickers for every occasion.</p>

    <!-- Scrollable sticker container -->
    <div
        class="sticker-scroll-container"
        on:mousedown={startDrag}
        on:mousemove={onDrag}
        on:mouseup={stopDrag}
        on:mouseleave={stopDrag}
    >
        <div class="sticker-container">
            {#each images as image, index}
                <div class="sticker-item">
                    <img src={image} alt={`Sticker ${index + 1}`} />
                    <div class="sticker-content">
                        <h3 class="sticker-name">Sticker {index + 1}</h3>
                        <p class="sticker-price">${prices[index]}</p>
                        <button class="add-to-cart-button">Add to Cart</button>
                    </div>
                </div>
            {/each}
        </div>
    </div>

    <!-- Button container for "Customize" and "View All" -->
    <div class="button-container">
        <button class="action-button">
            <a href="/experience">
                Customize Your Stickers 
            </a>
        </button>
        <button class="action-button">
            <a href="/shop">
                View All Stickers 
            </a>
        </button>
    </div>
</section>