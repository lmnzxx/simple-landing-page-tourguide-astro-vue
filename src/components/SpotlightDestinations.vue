<template>
  <section class="top-destinations">
    <div class="text-center">
      <h2>SPOTLIGHT DESTINATIONS</h2>
      <span></span>
      <p>
        Looking for your next great adventure? We can help. Here is a sampling of
        our most popular destinations. Experience private tours with authentic local flavour.
      </p>
    </div>

    <div class="destination-grid">
      <div
        v-for="(destination, index) in destinations"
        :key="index"
        class="destination-card"
        :style="{ backgroundImage: `url(${destination.image})` }"
      >
        <span>{{ destination.name }}</span>
      </div>
    </div>
  </section>
</template>

<script setup>
const destinations = [
  {
    name: 'Ulun Danu Beratan, Bedugul',
    image: '/images/slides.jpg'
  },
  {
    name: 'Tanah Lot, Tabanan',
    image: '/images/slides1.jpg'
  },
  {
    name: 'Uluwatu, Badung',
    image: '/images/slides.jpg'
  },
  {
    name: 'Pinggan, Kintamani',
    image: '/images/slides1.jpg'
  }
];
</script>

<style scoped>
.top-destinations {
  background: #fff;
}

.text-center {
  text-align: center;
  margin-bottom: 2rem;
  margin-top: 3rem;
}

.text-center h2 {
  font-size: 1.5rem;
  font-weight: 700;
  letter-spacing: 8px;
  margin-bottom: 1rem;
}

.text-center span {
  display: block;
  width: 480px;
  height: 2px;
  background: #ff7b01;
  margin: 0 auto;
  margin-bottom: 1rem;
}

.text-center p {
  font-size: 1rem;
  max-width: 700px;
  margin: 0 auto;
  color: #444;
  line-height: 1.6;
}

.destination-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 0;
}

.destination-card {
  position: relative;
  background-size: cover;
  background-position: center;
  height: 50vh;
  overflow: hidden;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: filter 0.3s ease-in-out;
}

.destination-card::before {
  content: "";
  position: absolute;
  inset: 0;
  background: rgba(0, 0, 0, 0.2);
  transition: background 0.3s;
}

.destination-card:hover::before {
  background: rgba(0, 0, 0, 0.5);
}

.destination-card span {
  position: relative;
  color: #fff;
  font-size: 1.2rem;
  font-weight: bold;
  text-align: center;
  z-index: 1;
  padding: 0 1rem;
}

@media (max-width: 768px) {
  .text-center h2 {
    font-size: 1.2rem;
  }

  .text-center p {
    font-size: 0.9rem;
  }

  .destination-card span {
    font-size: 1rem;
  }
}

@media (max-width: 480px) {
  .text-center h2 {
    font-size: 1rem;
  }

  .text-center p {
    font-size: 0.8rem;
  }

  .text-center span {
    width: 360px;
  }

  .destination-card span {
    font-size: 0.9rem;
  }
}
</style>
