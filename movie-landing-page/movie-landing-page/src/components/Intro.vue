<template>
  <section id="intro" class="intro-section">
    <h2 class="intro-title">Welcome to Movie Hub</h2>
    <p class="intro-text">
      Discover the latest and greatest films, explore detailed descriptions, and curate your own watchlist.  
      Search, add, or remove movies effortlessly—all in one place.
    </p>
  </section>
</template>

<script>
export default {
  name: 'Intro'
}
</script>

<style scoped>
.intro-section {
  padding: 60px 20px;
  text-align: center;
  background-color: #f5f5f5;
}

.intro-title {
  font-size: 2.5rem;
  margin-bottom: 20px;
  color: #333;
}

.intro-text {
  font-size: 1.125rem;
  max-width: 800px;
  margin: 0 auto;
  line-height: 1.6;
  color: #555;
}
</style>
