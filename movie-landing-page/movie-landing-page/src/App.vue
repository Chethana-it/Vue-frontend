<template>
  <div id="app">
    <Header />
    <Hero />
    <Intro />
    <MovieGrid />
    <Contact/>
    <Footer/>
  </div>
</template>

<script>
import Header   from './components/Header.vue'
import Hero     from './components/Hero.vue'
import Intro    from './components/Intro.vue'
import MovieGrid from './components/MovieGrid.vue'
import Contact  from './components/Contact.vue'
import Footer   from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    Header,
    Hero,
    Intro,
   MovieGrid,
     Contact,
    Footer
  }
}
</script>
