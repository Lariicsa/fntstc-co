<template>
  <header class="header">
    <div class="header-top">
      <ul class="container in header-top-items">
        <li>
          <a href="#">Ingresar</a>
        </li>
        <li>
          <a href="#">Registrarse</a>
        </li>
        <li>
          <a href="#">Carrito</a>
        </li>
      </ul>
    </div>
    <nav class="navbar">
      <div class="navbar-wrap container in">
        <a href="/">
          <img
            src="https://fantasticocomic.com/img/logo-fantastico-beta.png"
            alt="tu canton"
            height="40"
          />
        </a>
        <Finder />
        <div class="navbar-social">
          <div class="navbar-social-item fb"></div>
          <div class="navbar-social-item tw"></div>
        </div>
      </div>
    </nav>
  </header>
</template>

<style lang="scss">
@import "../scss/index.scss";
@import "../scss/shared/_mixins.scss";

.header {
  background-color: $secondary;
  border-bottom: 0.1rem solid $snow;
  display: flex;
  flex-direction: column;
  height: auto;
  width: 100%;

  &-top {
    background-color: $blue-top;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 2.4rem;
    width: 100%;

    &-items {
      list-style-type: none;
      display: flex;
      align-items: center;
      justify-content: flex-end;
      margin: 0;
      padding: 0;
      width: 100%;

      & > li {
        margin: 0 0.6rem;
        & > a {
          display: inline-block;
          font-size: $small-size;
          font-weight: $bold;
          color: $snow;
          text-decoration: none;
          cursor: pointer;
        }
      }
    }
  }

  .navbar {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    padding: 0;
    flex-wrap: wrap;

    a {
      text-decoration: none;
      font-weight: $regular;
      color: $blackio;
      & > img {
        width: 28.4rem;
        height: 9rem;
      }
    }

    &-social {
      display: flex;
      align-items: center;
      justify-content: space-between;
      height: 5rem;
      width: 100%;
      max-width: 10rem;
      &-item {
        background-color: $primary;
        border: 0.1rem solid $snow;
        background-position: center;
        border-radius: 100%;
        display: flex;
        height: 4rem;
        width: 4rem;

        &.fb {
          @include icon-set("fb");
          background-size: 36%;
        }
        &.tw {
          @include icon-set("tw");
          background-size: 40%;
        }

        &:hover {
          background-color: $blackio;
          cursor: pointer;
        }
      }
    }

    &-wrap {
      align-items: center;
      @include tablet {
        flex-direction: column;
        justify-content: space-between;
        align-items: center;
      }
      & > * {
        @include tablet {
          margin: 0.8rem 0;
        }
      }
    }
  }
}
</style>

<script>
import Finder from "./Finder.vue";
export default {
  name: "Header",
  components: {
    Finder
  }
};
</script>