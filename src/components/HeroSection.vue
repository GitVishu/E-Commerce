<template>
  <div class="banner" aria-label="Shop now">
    <div class="banner__grid">
      <div aria-hidden="true">
        <figure
          class="banner__figure"
          :style="{ backgroundImage: `url(${currentImage})` }"
        ></figure>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HeroSection",
  data() {
    return {
      // Load images using require() with error handling
      images: [
        require("@/assets/banner6.jpg"),
        require("@/assets/banner4.jpg"),
        require("@/assets/banner5.jpg"),
      ],
      currentIndex: 0,
      intervalId: null,
    };
  },
  computed: {
    currentImage() {
      return this.images[this.currentIndex];
    },
  },
  mounted() {
    this.startSlideShow();
  },
  methods: {
    startSlideShow() {
      // Automatically change images every 3 seconds
      this.intervalId = setInterval(() => {
        this.currentIndex = (this.currentIndex + 1) % this.images.length;
      }, 3000); // Adjust interval as needed
    },
    stopSlideShow() {
      if (this.intervalId) {
        clearInterval(this.intervalId);
      }
    },
  },
  beforeUnmount() {
    this.stopSlideShow();
  },
};
</script>

<style scoped>
/* Banner Styles */
.banner {
  width:100%;
  /* max-width:600px; */
  height: auto; /* Maintain aspect ratio */
  margin: 0 auto; /* Center align */
  display: block;
  text-decoration: none;
  color: inherit;
  overflow: hidden;
  background-color: hsl(0, 0%, 100%);
  box-shadow: 0 0 0 1px hsla(230, 13%, 9%, 0.05),
    0 0.3px 0.4px hsla(230, 13%, 9%, 0.02),
    0 0.9px 1.5px hsla(230, 13%, 9%, 0.045),
    0 3.5px 6px hsla(230, 13%, 9%, 0.09);
  border-radius: 0.375em;
  transition: 0.3s;
}

.banner__grid {
  display: flex;
  flex-direction: column;
}

.banner__figure {
  height: 0;
  /* width: 100%; */
  padding-bottom: 50%;
  transition: 0.3s ease-in-out;
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
}

.banner__text {
  padding: 1.5rem;
}

.banner__link-wrapper {
  margin-top: 1rem;
}
@media (max-width: 600px) {
    .banner {
        width: 100%; /* Increase width on smaller screens */
    }
}
</style>
