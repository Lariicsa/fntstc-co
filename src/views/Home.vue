<template>
  <div class="space" id="app">
    <Header></Header>
    <div class="container">
      <div class="row center">
        <Carousel></Carousel>
      </div>
      <div class="row">
        
      </div>
    </div>
    <Footer></Footer>
  </div>
</template>

<script>
import Carousel from "../components/Carousel.vue";
import Header from "../components/Header.vue";
import Footer from "../components/Footer.vue";

export default {
  name: "app",
  components: {
    Carousel,
    Header,
    Footer
  },
  data() {
    return {
      selectedValue: ""
    };
  },
  methods: {
    changeValue: function(newValue) {
      this.selectedValue = newValue;
    }
  }
};
</script>