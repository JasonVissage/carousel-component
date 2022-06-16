<template>
  <div class="app">
    <carousel @next="next" @prev="prev">
      <carousel-slide
        v-for="(slide, index) in slides"
        :key="slide"
        :index="index"
        :visibleSlide="visibleSlide"
      >
        <img :src="slide" />
      </carousel-slide>
    </carousel>
  </div>
</template>

<script>
import Carousel from './components/Carousel.vue';
import CarouselSlide from './components/CarouselSlide.vue';
export default {
  data() {
    return {
      slides: [
        'https://picsum.photos/id/230/600/350',
        'https://picsum.photos/id/231/600/350',
        'https://picsum.photos/id/232/600/350',
        'https://picsum.photos/id/233/600/350',
        'https://picsum.photos/id/234/600/350',
        'https://picsum.photos/id/235/600/350',
      ],
      visibleSlide: 0,
    };
  },
  computed: {
    slidesLength() {
      return this.slides.length;
    },
  },
  methods: {
    next() {
      if (this.visibleSlide >= this.slidesLength - 1) {
        this.visibleSlide = 0;
      } else {
        this.visibleSlide++;
      }
    },
    prev() {
      if (this.visibleSlide <= 0) {
        this.visibleSlide = this.slidesLength - 1;
      } else {
        this.visibleSlide--;
      }
    },
  },
  components: {
    Carousel,
    CarouselSlide,
  },
};
</script>

<style scr="./index.css"></style>
