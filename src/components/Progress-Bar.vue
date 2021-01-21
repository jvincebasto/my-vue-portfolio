<template>
  <div class="progress-bar">
    <div>&nbsp;</div>
    <span class="progress-bar--center-line">&nbsp;</span>
  </div>
</template>

<script></script>

<style scoped lang="scss">
@use "./../sass/abstracts/abstracts" as abs;

.progress-bar {
  height: 2.2rem;
  width: 40rem;

  border-radius: 10rem;
  border: 0.3rem solid black;

  display: flex;
  align-items: center;
  overflow: hidden;

  position: relative;

  display: flex;
  align-items: center;

  & div {
    height: 120%;
    margin-left: -1rem;
    background-image: linear-gradient(
      to right,
      abs.$vars-c-lightblue,
      rgba(abs.$vars-c-lightblue, 0.8) 90%,
      rgba(abs.$vars-c-lightblue, 0)
    );
  }

  &--css div {
    width: 80%;
  }
  &--js div {
    width: 78%;
  }
  &--php div {
    width: 68%;
  }
  &--sql div {
    width: 75%;
  }
  &--laravel div {
    width: 65%;
  }
  &--vue div {
    width: 75%;
  }

  &--center-line {
    width: 50%;
    position: absolute;
    top: 0;
    left: 0;

    border-right: 0.1rem dashed rgba(0, 0, 0, 0.8);

    // background: orange;
  }
}
</style>
