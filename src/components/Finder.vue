<template>
  <div class="finder">
    <input type="text" value="Buscar" />
    <span class="finder-icon"></span>
  </div>
</template>

<style lang="scss">
@import "../scss/index.scss";
@import "../scss/shared/_mixins.scss";

.finder {
  background-color: $snow;
  border: 0.1rem solid $border-grey;
  border-radius: 0.8rem;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 4.6rem;
  width: 100%;
  max-width: 44rem;
  &-icon {
    @include icon-set("finder");
    background-size: 28%;
    background-position: center;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 4.6rem;
    width: 5.3rem;
  }
  input {
    display: block;
    border: none;
    border-top-left-radius: 0.8rem;
    border-bottom-left-radius: 0.8rem;
    padding: 1rem 1.6rem;
    width: calc(100% - 53px);
    height: 100%;
  }
}
</style>

