<template>
  <section class="testimonials" id="testimonials">
    <h2 class="section-title">What Our Travelers Say</h2>
    <p class="section-subtitle">Real experiences from happy customers</p>

    <div class="container">
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
  </section>
</template>

<script setup>
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
  }
]
</script>

<style scoped>
.testimonials {
  padding: 60px 20px;
  background-color: #f9f9f9;
  text-align: center;
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

.testimonial-card {
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

@media (max-width: 768px) {
  .testimonial-container {
    flex-direction: column;
    align-items: center;
  }
}
</style>
