<template>
  <section class="testimonials" id="testimonials">
    <div class="container-1200">
      <h2 class="section-title">What Our Travelers Say</h2>
      <p class="section-subtitle">Real experiences from happy customers</p>

      <div class="carousel-container">
        <div class="carousel-wrappper">
          <div class="carousel-gradient left"></div>
          <div class="carousel-gradient right"></div>

          <div class="carousel-track" ref="track">
            <div class="testimonial-card" v-for="(item, index) in testimonials" :key="index">
              <p class="quote">"{{ item.message }}"</p>
              <div class="profile">
                <img :src="item.image" :alt="item.name" class="avatar" />
                <div>
                  <p class="name">{{ item.name }}</p>
                  <p class="location">{{ item.location }}</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { onMounted, ref, onBeforeUnmount } from 'vue';

const testimonials = [
  {
    name: "Jessica W.",
    location: "California, USA",
    message: "It was an unforgettable experience! The guide was super friendly and informative. Highly recommended.",
    image: "/images/profile.jpg"
  },
  {
    name: "Aditya K.",
    location: "Jakarta, Indonesia",
    message: "Pelayanan sangat ramah dan profesional. Semua tour-nya bisa dikustom! Suka banget!",
    image: "/images/profile.jpg"
  },
  {
    name: "Marie C.",
    location: "Paris, France",
    message: "Bali is magical and this tour made it even more special. Thank you for the amazing journey!",
    image: "/images/profile.jpg"
  },
    {
    name: "Jessica W.",
    location: "California, USA",
    message: "It was an unforgettable experience! The guide was super friendly and informative. Highly recommended.",
    image: "/images/profile.jpg"
  },
  {
    name: "Aditya K.",
    location: "Jakarta, Indonesia",
    message: "Pelayanan sangat ramah dan profesional. Semua tour-nya bisa dikustom! Suka banget!",
    image: "/images/profile.jpg"
  },
  {
    name: "Marie C.",
    location: "Paris, France",
    message: "Bali is magical and this tour made it even more special. Thank you for the amazing journey!",
    image: "/images/profile.jpg"
  }
];

const track = ref(null);
let pos = 0;
let animationFrame;
let isPaused = false;

const scrollSpeed = 0.5;

function animateScroll() {
  if (!isPaused && track.value) {
    pos += scrollSpeed;
    track.value.scrollLeft = pos;

    if (pos >= track.value.scrollWidth / 2) {
      pos = 0;
      track.value.scrollLeft = 0;
    }
  }
  animationFrame = requestAnimationFrame(animateScroll);
}

function pauseScroll() {
  isPaused = true;
}

function resumeScroll() {
  isPaused = false;
}

onMounted(() => {
  if (track.value) {
    track.value.addEventListener('mouseenter', pauseScroll);
    track.value.addEventListener('mouseleave', resumeScroll);
  }
  animationFrame = requestAnimationFrame(animateScroll);
})

onBeforeUnmount(() => {
  cancelAnimationFrame(animationFrame);
  if (track.value) {
    track.value.removeEventListener('mouseenter', pauseScroll);
    track.value.removeEventListener('mouseleave', resumeScroll);
  }
})
</script>

<style scoped>
.container-1200 {
  max-width: 1200px;
  margin: 0 auto;
}

.testimonials {
  padding: 60px 20px;
  background-color: #f9f9f9;
  text-align: center;
  position: relative;
  overflow: hidden;
}

.section-title {
  font-size: 2.5em;
  color: #ff7b01;
  margin-bottom: 10px;
  margin-top: 0;
}

.section-subtitle {
  font-size: 1.2em;
  color: #777;
  margin-bottom: 40px;
}

.container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 30px;
}

.carousel-container {
  overflow-x: hidden;
}

.carousel-wrappper {
  position: relative;
  overflow: hidden;;
}

.carousel-track {
  display: flex;
  gap: 20px;
  padding-bottom: 10px;
  scroll-snap-type: x mandatory;
  scroll-behavior: smooth;
  overflow-x: auto;
  scrollbar-width: none;
  -ms-overflow-style: none;
}

.carousel-track::-webkit-scrollbar {
  display: none;
}

.testimonial-card {
  flex: 0 0 auto;
  scroll-snap-align: center;
  background-color: #fff;
  max-width: 300px;
  padding: 25px 20px;
  border-radius: 15px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
  text-align: left;
  transition: transform 0.3s ease;
}

.testimonial-card:hover {
  transform: translateY(-5px);
  transition: transform 0.3s ease;
}

.quote {
  font-style: italic;
  color: #555;
  margin-bottom: 20px;
}

.profile {
  display: flex;
  align-items: center;
  gap: 15px;
}

.avatar {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  object-fit: cover;
}

.name {
  font-weight: bold;
  color: #333;
}

.location {
  font-size: 0.9em;
  color: #999;
}

.carousel-gradient {
  position: absolute;
  top: 0;
  bottom: 0;
  width: 480px;
  pointer-events: none;
  z-index: 10;
}

.carousel-gradient.left {
  left: 0;
  background: linear-gradient(to right, #f9f9f9, rgba(249, 249, 249, 0));
}

.carousel-gradient.right {
  right: 0;
  background: linear-gradient(to left, #f9f9f9, rgba(249, 249, 249, 0));
}

@media (max-width: 768px) {
  .testimonial-container {
    flex-direction: column;
    align-items: center;
  }
}
</style>
