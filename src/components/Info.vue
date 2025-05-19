<template>
  <section class="info-section" id="about">
    <div class="info-top">
      <h2 class="number">8.752</h2>
      <p class="label">TRAVELER SERVED</p>
    </div>

    <div class="info-middle">
      <p class="stats">12 Professional Local Guides, and 18 Unit of Transportation</p>
      <p class="description">
        Let’s discover Bali with us!
      </p>
      <p class="description">
        With 4 years of experience in tourism,
        our tours package offer you a unique and personalized experience in any destination.      </p>
    </div>

    <div class="info-bottom">
      <div class="feature">
        <img src="/icons/medal.png" alt="Medal Icon" loading="lazy" />
        <p class="caption">CHOSEN PROFESSIONAL GUIDE</p>
      </div>
      <div class="feature">
        <img src="/icons/thumbsup.png" alt="Thumbsup Icon" loading="lazy" />
        <p class="caption">FLEXIBLE CANCELATION</p>
      </div>
      <div class="feature">
        <img src="/icons/lamp.png" alt="Lamp Icon" loading="lazy" />
        <p class="caption">EVERY TOUR PRIVATE AND CUSTOMIZABLE</p>
      </div>
      <div class="feature">
        <img src="/icons/customer-services.png" alt="Customer Service Icon" loading="lazy" />
        <p class="caption">24/7 CUSTOMER SUPPORT</p>
      </div>
    </div>
  </section>
</template>

<script setup>
</script>

<style scoped>
.info-section {
  text-align: center;
  padding: 50px 0px 0px 0px;
}

.info-top .number {
  font-size: 4em;
  font-weight: bold;
  margin: 0;
  color: #ffb547;
}

.info-top .label {
  font-size: 2em;
  font-weight: 600;
  color: #ff7b01;
  margin-top: 10px;
}

.info-middle {
  margin-top: 60px;
  margin-bottom: 40px;
  margin-left: 100px;
  margin-right: 100px;
}

.info-middle .stats {
  font-size: 2.5em;
  font-weight: bold;
  margin-bottom: 20px;
}

.info-middle .description {
  margin: 0;
  font-size: 1em;
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
  color: #444;
}

.info-bottom {
  background-color: #dedede;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 65px;
  padding: 50px 100px;
}

.feature {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 200px;
}

.feature img {
  height: 50px;
  margin-bottom: 10px;
}

.feature .caption {
  font-size: 1em;
  font-weight: bold;
  color: #333;
  text-align: center;
}

@media (max-width: 768px) {
  .info-top .number {
    font-size: 2.5em;
  }
  .info-top .label {
    font-size: 1.5em;
  }
  .info-middle .stats {
    font-size: 1.5em;
    padding: 0 100px;
  }
  .info-middle .description {
    font-size: 0.9em;
    padding: 0 100px;
  }
  .info-middle {
    margin: 30px 0;
  }
  .info-bottom {
    padding: 30px 100px;
  }
}
</style>
