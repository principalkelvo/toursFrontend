<template>
  <section class="mb-2 p-0">
    <!--carousel-->
      <Carousel
        :navigation="false"
        :pagination="false"
        :startAutoPlay="true"
        :timeout="10000"
        class="carousel"
        v-slot="{ currentSlide }"
      >
      <!-- overlay -->
    <div class="overlay"></div>

        <!--the captions-->
        <div class="has-text-left captions">
          <div class="background-captions">
            <p class="title mb-4 is-uppercase">Welcome to <br> Pokot</p>
            <p class="subtitle">Kenya spectacular sceneries</p>
          </div>
        </div>

        <!--background images-->
        <Slide v-for="(slide, index) in carouselSlides" :key="index">
          <div
            v-show="currentSlide === index + 1"
            class="slide-info image is-fullwidth"
          >
            <img
              :src="require(`../assets/${slide}.jpg`)"
              alt=""
              class=""
            />
          </div>
        </Slide>
    
      </Carousel>
  </section>
</template>

<script>
import axios from "axios";
import Carousel from "../components/Carousel.vue";
import Slide from "../components/Slide.vue";

export default {
  name: "Fullwidth",
  data() {},
  components: {
    Carousel,
    Slide,
  },
  setup() {
    const carouselSlides = [
      "bg- 1",
      "bg- 2",
      "bg- 3",
      "bg- 4",
      "bg- 5",
      "bg- 6",
      "bg- 7",
    ];
    return { carouselSlides };
  },
  mounted() {},
  methods: {},
};
</script>
<style lang="scss" scoped>
.overlay{
  background: linear-gradient(54deg, #660746 0%, #66074628 100%, #660746ee 100%);;
  width: 100%;
  height: 100%;
  opacity: .6;
  z-index: 1;
  border-radius: 10px;
}
.carousel {
  position: relative;
  height: 20vh;
  display: flex;
  
  // justify-content: center;
  .captions {
    position: absolute;
    z-index: 2;
    width: 50%;
    bottom: 20%;
    left: 3%;


    p {
      color: rgb(255, 255, 255);
      font-weight: 900;
      text-shadow: 1px 0px 5px rgba(0, 0, 0);
    }
  }
  //   .background-captions {
  //     background: rgba(0, 0, 0, 0.5);
  //     transition: 2s;
  //     padding-top: 10px;
  //     padding-bottom: 20px;
  //     border-radius: 20px;
  //   }

  .slide-info {
    position: absolute;

    top: 0;
    left: 0;
    width: 100%;
    max-height: 100%;
    height: 100%;
    
    img {
      border-radius: 10px;
      min-width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }
}
@media (max-width: 768px) {
  .mb-6{
      margin-bottom: 1em !important;
    }
  section{
    padding: 0;

  .captions{ 
    .title{
      font-size: 1.2rem;
    }
    .subtitle{
      font-size: .8rem;
    }
    
    p{
      font-weight:600;
    }
  }
  }
  
  
}
</style>
