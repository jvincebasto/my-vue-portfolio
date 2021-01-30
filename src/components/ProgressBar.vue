<template>
  <div class="progress-bar progress-bar--container">
    <div class="progress-bar--bg" :style="$attrs.pgBarFill"></div>
    <div class="progress-bar--border"></div>
    <div class="progress-bar--center-line"></div>
  </div>
</template>

<script>
export default {
  inheritAttrs: false
};
</script>

<style scoped lang="scss">
@use "./../sass/abstracts/abstracts" as abs;

.progress-bar {
  &--container {
    height: 2.4rem;
    min-width: 20rem;
    width: 100%;
    border-radius: 10rem;

    position: relative;
    overflow: hidden;
  }

  & > * {
    display: block;
    height: inherit;
    width: inherit;

    border-radius: inherit;
    border: 0.4rem solid abs.$vars-c-black;

    position: absolute;
    top: 0;
    left: 0;
  }
  &--bg {
    width: unset;
  }

  &--border {
    border-color: abs.$vars-c-black;
  }

  &--bg {
    border-radius: 0;
    border: none;

    background-image: linear-gradient(
      to right,
      abs.$vars-c-secondary,
      rgba(abs.$vars-c-secondary, 0.8) 90%,
      rgba(abs.$vars-c-secondary, 0)
    );
  }

  &--css &--bg {
    width: 80%;
  }
  &--js &--bg {
    width: 78%;
  }
  &--php &--bg {
    width: 68%;
  }
  &--sql &--bg {
    width: 75%;
  }
  &--laravel &--bg {
    width: 65%;
  }
  &--vue &--bg {
    width: 75%;
  }

  &--center-line {
    border-radius: 0;
    border: none;

    width: 50%;
    border-right: 0.1rem dashed rgba(0, 0, 0, 0.8);

    // background: orange;
  }
}
</style>
