<template>
  <section class="about-section">
    <div class="content">
      <h2>About Us</h2>
      <p>
        We are dedicated to providing innovative solutions that encourage
        sustainability and help people make a positive impact in their daily
        lives. Our mission is to create awareness and provide tools that make
        recycling and waste reduction easy, accessible, and rewarding.
      </p>
      <p>
        Our team is committed to developing strategies that help individuals and
        businesses alike embrace sustainable practices. Join us on our journey
        to a cleaner, greener future.
      </p>
      <button class="learn-more">Learn More</button>
    </div>
    <div class="image-container">
      <img :src="require('@/assets/about.jpg')" alt="About Us" />
    </div>
  </section>
</template>

<script>
export default {
  name: "About",
};
</script>

<style scoped>
.about-section {
  display: flex;
  align-items: center;
  gap: 3rem;
  padding: 4rem 2rem;
  background-color: #e6e6fa;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  overflow: hidden;
}

.content {
  flex: 1;
  max-width: 600px;
  animation: fadeInLeft 1s ease-in-out;
}

h2 {
  font-size: 2.5rem;
  color: #4e4537;
  margin-bottom: 1rem;
  position: relative;
}

h2::after {
  content: "";
  display: block;
  width: 50px;
  height: 4px;
  background-color: #008765;
  margin-top: 8px;
  border-radius: 4px;
}

p {
  font-size: 1.1rem;
  color: #4e4537;
  line-height: 1.8;
  margin-bottom: 1rem;
}

.learn-more {
  display: inline-block;
  margin-top: 1.5rem;
  padding: 0.75rem 1.5rem;
  font-size: 1rem;
  color: white;
  background-color: #008765;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.3s ease;
  text-transform: uppercase;
}

.learn-more:hover {
  background-color: #008765;
  transform: translateY(-2px);
}

.image-container {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  animation: fadeInRight 0.8s ease-in-out;
}

.image-container img {
  width: 100%;
  max-width: 500px;
  border-radius: 12px;
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.15);
  transition: transform 0.3s ease;
}

.image-container img:hover {
  transform: scale(1.05);
}

/* Animations */
@keyframes fadeInLeft {
  from {
    opacity: 0;
    transform: translateX(-50px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes fadeInRight {
  from {
    opacity: 0;
    transform: translateX(50px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

/* Responsive Styling */
@media (max-width: 768px) {
  .about-section {
    flex-direction: column;
    text-align: center;
  }

  .content,
  .image-container {
    max-width: 100%;
  }

  .image-container {
    margin-top: 2rem;
  }
}
</style>
