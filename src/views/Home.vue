<template>
  <div class="home">
    <Header />
    <Hero />
    <CarouselProduct />
    <Gallery />
    <Partner />
    <Footer />
  </div>
</template>

<script>
import Header from '@/components/Header.vue';
import Hero from '@/components/Hero.vue';
import CarouselProduct from '@/components/CarouselProduct.vue';
import Gallery from '@/components/Gallery.vue';
import Partner from '@/components/Partner.vue';
import Footer from '@/components/Footer.vue';
// import carousel from 'vue-owl-carousel';

export default {
  name: 'Home',
  components: {
    Header,
    Hero,
    CarouselProduct,
    Gallery,
    Partner,
    Footer
    // carousel
  }
}
</script>
