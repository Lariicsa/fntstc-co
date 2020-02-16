<template>
  <div class="space" id="app">
    <Header></Header>
    <div class="container">
      <div class="row center">
        <h2>Visita sin costo las casa que más te gusten</h2>
      </div>
      <div class="row center">
        <p>Elige la fecha y en qué momento del día:</p>
      </div>
      <div class="container">
        <div class="row">

        </div>
        <div class="row center">
          <ul class="row center">
            <OptionButton name="options" :checked="false"  @change="changeValue">Por la mañana</OptionButton>
            <OptionButton :checked="true" name="options"  @change="changeValue">Por la tarde</OptionButton>
          </ul>
      </div>
      </div>
      <div class="container">
        <div class="row">
          <SendForm />
        </div>
        <div class="row center">
          <p>Al agendar, estás aceptando nuestro <a href="https://www.tucanton.com/avisoPrivacidad">Aviso de privacidad</a></p>
        </div>
      </div>
    </div>
    <Footer></Footer>
  </div>
</template>

<script>

import Header from '../components/Header.vue'
import Footer from '../components/Footer.vue'

export default {
  name: "app",
  components: {
    Header,
    Footer
  },
  data() {
    return {
      selectedValue: ''
    };
  },
  methods: {
    changeValue: function(newValue) {
      this.selectedValue = newValue;
    }
  }
};
</script>