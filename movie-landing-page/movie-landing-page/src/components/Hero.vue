<template>
  <section id="hero" class="hero-section">
    <div class="slider">
     
      <img 
        :src="`/assets/${images[currentIndex]}`" 
        alt="Slide Image" 
        class="hero-image"
      />
      
      <button class="prev" @click="prevSlide">‹</button>
      <button class="next" @click="nextSlide">›</button>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Hero',
  data() {
    return {
      // slideshow සඳහා images filenames list
      images: [
        'Batman.jpg',
        'Wild West.jpg',
        'Spiderman.jpg',
        'Header Image.jpg'
      ],
      currentIndex: 0,   
      intervalId: null   
    }
  },
  methods: {
    nextSlide() {
      this.currentIndex = 
        (this.currentIndex + 1) % this.images.length;
    },
    prevSlide() {
      this.currentIndex = 
        (this.currentIndex - 1 + this.images.length) % this.images.length;
    }
  },
  mounted() {
   
    this.intervalId = setInterval(() => {
      this.nextSlide();
    }, 5000);
  },
  beforeUnmount() {
   
    clearInterval(this.intervalId);
  }
}
</script>

<style scoped>
.hero-section {
  position: relative;
  width: 100%;
  height: 80vh;
  overflow: hidden;
}
.slider {
  width: 100%;
  height: 100%;
}
.hero-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: opacity 1s ease-in-out;
}
/* (Optional) Prev / Next Buttons */
.prev, .next {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(0,0,0,0.5);
  color: white;
  border: none;
  font-size: 2rem;
  padding: 0 10px;
  cursor: pointer;
}
.prev { left: 20px; }
.next { right: 20px; }
</style>
