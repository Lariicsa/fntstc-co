<template>
  <div class="space" id="app">
    <Header></Header>
    <div class="container">
      <div class="row center">
        <Carousel></Carousel>
      </div>
      <div class="row container-in">
        <div class="row">
          <h3>Artículos nuevos</h3>
          <ul class="cards">
            <li v-for="(item, index) in items.slice(10,16)" :key="index">
              <span>{{ item.name }}</span>
              <a href="#">
                <img v-bind:src="item.image_url" />
              </a>
            </li>
          </ul>
        </div>
      </div>
      <div class="row container-in">
        <hr />
      </div>
      <div class="row container-in">
        <div class="row">
          <h3>Recomendaciones</h3>
          <ul class="cards">
            <li class="no-border" v-for="(item, index) in items.slice(10,16)" :key="index">
              <a href="#">
                <img v-bind:src="item.image_url" />
                <h4>{{ item.name }}</h4>
                <p>{{item.tagline}}</p>
                <strong>${{item.target_og}}</strong>
              </a>
            </li>
          </ul>
        </div>
      </div>
    </div>
    <Footer></Footer>
  </div>
</template>

<script>
import Carousel from "../components/Carousel.vue";
import Header from "../components/Header.vue";
import Footer from "../components/Footer.vue";
import axios from "axios";

export default {
  name: "app",
  components: {
    Carousel,
    Header,
    Footer
  },
  data() {
    return {
      items: {}
    };
  },

  created() {
    axios
      .get(`https://ih-beer-api.herokuapp.com/beers`)
      .then(response => {
        this.items = response.data;
      })
      .catch(e => {
        this.errors.push(e);
      });
  }
};
</script>

<style lang="scss">
@import "../scss/index.scss";
@import "../scss/shared/_mixins.scss";

</style>