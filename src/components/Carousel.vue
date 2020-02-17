<template>
  <div class="carousel">
    <div class="carousel-controls">
      <a class="carousel-controls-arrow prev" @click="prev" href="#"></a> ||
      <a class="carousel-controls-arrow next" @click="next" href="#"></a>
    </div>
    <transition-group name="slide-fade" tag="div" class="row">
      <div v-for="number in [currentNumber]" :key="number" class="carousel-image-wrapper">
        <img
          :src="currentImage"
          v-on:mouseover="stopRotation"
          v-on:mouseout="startRotation"
          class="carousel-image"
        />
      </div>
    </transition-group>
  </div>
</template>
<script>
export default {
  name: "carousel",
  data() {
    return {
      images: [
        "https://fantasticocomic.com/img/carrousel/banner2.jpg",
        "https://fantasticocomic.com/img/carrousel/banner7.jpg",
        "https://fantasticocomic.com/img/carrousel/banner9.jpg"
      ],
      currentNumber: 0,
      timer: null
    };
  },

  mounted: function() {
    this.startRotation();
  },

  methods: {
    startRotation: function() {
      this.timer = setInterval(this.next, 5000);
    },

    stopRotation: function() {
      clearTimeout(this.timer);
      this.timer = null;
    },

    next: function() {
      this.currentNumber += 1;
    },
    prev: function() {
      this.currentNumber -= 1;
    }
  },

  computed: {
    currentImage: function() {
      return this.images[Math.abs(this.currentNumber) % this.images.length];
    }
  }
};
</script>

<style lang="scss" scoped>
@import "../scss/index.scss";
@import "../scss/shared/_mixins.scss";

.carousel {
  display: flex;
  height: 100%;
  max-height: 32rem;
  width: 100%;
  max-width: 97rem;
  position: relative;

  &-controls {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-top: -16rem;
    height: 100%;
    width: 100%;
    position: absolute;
    top: 42%;
    left: 0;
    z-index: 10;
    @include tablet {
      padding: 0 1.6rem;
    }

    &-arrow {
      position: relative;
      &:hover {
        background-color: #d9534f;
      }
      &.prev {
        &:after,
        &:before {
          content: "";
          width: 7px;
          height: 20px;
          position: relative;
          background: #428bca;
          display: block;
          position: absolute;
          left: 0;
        }
        &:before {
          transform: rotate(-135deg);
          top: 8px;
        }
        &:after {
          transform: rotate(-45deg);
          top: 18px;
        }
      }
      &.next {
        &:after,
        &:before {
          content: "";
          width: 7px;
          height: 20px;
          position: relative;
          background: #428bca;
          display: block;
          position: absolute;
          left: 0;
        }
        &:before {
          transform: rotate(-45deg);
          top: 8px;
        }
        &:after {
          transform: rotate(-135deg);
          top: 18px;
        }
      }
    }
  }

  &-image {
    display: block;
    margin: 0 auto;
    height: 32rem;
    width: 100%;
    &-wrapper {
      position: relative;
      overflow: hidden;
      width: 100%;
    }
  }
}

.slide-fade-enter-active {
  transition: all 0.3s ease;
}

.slide-fade-leave-to {
  left: 0;
  transform: translate3d(0, 0, 0);
}

.slide-fade-enter,
.slide-fade-leave-to {
  transform: translateX(10px);
  opacity: 0;
}
</style>