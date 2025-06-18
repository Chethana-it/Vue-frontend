<template>
  <header class="site-header">
    <div class="logo">
      <img src="/assets/Logo White.svg" alt="Logo" />
    </div>

    <nav class="main-nav" :class="{ open: isMenuOpen }">
      <ul>
        <li><a href="#hero">Home</a></li>
        <li><a href="#movies">Movies</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
    </nav>

    <div class="hamburger" @click="toggleMenu">
      <span></span>
      <span></span>
      <span></span>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      isMenuOpen: false,
    };
  },
  methods: {
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen;
    },
  },
};
</script>

<style scoped>
.site-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px;
  background-color: #000;
  color: white;
}
.logo img {
  height: 40px;
}
.main-nav ul {
  display: flex;
  gap: 20px;
  list-style: none;
}
.main-nav a {
  color: white;
  text-decoration: none;
}
.hamburger {
  display: none;
  flex-direction: column;
  gap: 5px;
  cursor: pointer;
}
.hamburger span {
  width: 25px;
  height: 3px;
  background: white;
}

/* Responsive */
@media (max-width: 768px) {
  .main-nav {
    display: none;
  }
  .main-nav.open {
    display: block;
    position: absolute;
    top: 70px;
    background: #111;
    width: 100%;
    padding: 20px;
  }
  .hamburger {
    display: flex;
  }
}
</style>
