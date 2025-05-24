<template>
    <section class="hero-section" id="home">
        <div class="slideshow">
            <img :src="currentImage" loading="lazy" decoding="async" alt="Bali top destinations" class="hero-image" />
            <div class="overlay">
                <h1>Let's explore your tour destination with us</h1>
                <a href="#destinations" class="explore-btn">Explore Now</a>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted, computed } from 'vue';

const images = [
    '/images/slides.jpg',
    '/images/slides1.jpg'
];

const currentIndex = ref(0);

const currentImage = computed(() => images[currentIndex.value]);

let interval;

onMounted(() => {
    interval = setInterval(() => {
        currentIndex.value = (currentIndex.value + 1) % images.length;
    }, 10000); // 4 detik tiap slide
});

onUnmounted(() => {
    clearInterval(interval);
});
</script>

<style scoped>
.hero-section {
  width: 100%;
  height: 75vh;
  position: relative;
  overflow: hidden;
}

.slideshow {
  position: relative;
  width: 100%;
  height: 100%;
}

.hero-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: opacity 1s ease-in-out;
}

.overlay {
  position: absolute;
  max-width: 1200px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: left;
  color: white;
  z-index: 10;
}

.overlay h1 {
  font-size: 3rem;
  max-width: 700px;
  margin: 0 auto 2rem;
  line-height: 1.3;
}

.explore-btn {
  padding: 1rem 2.5rem;
  background-color: #ffcd82cc;
  color: #000;
  font-weight: bold;
  border-radius: 25px;
  text-decoration: none;
  transition: background 0.3s;
}

.explore-btn:hover {
  background-color: #ffb03a;
}

@media (max-width: 768px) {
    .hero-section {
        height: 90vh;
    }
    .overlay h1 {
        font-size: 2rem;
    }
    .explore-btn {
        padding: 0.3rem 1.2rem;
        font-size: 1rem;
    }
    .hero-image {
        height: 90vh;
    }
    
}
</style>
