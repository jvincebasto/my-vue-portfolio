<template>
  <template v-if="type(btnType)">
    <a class="btn btn--primary">
      <slot name="title">Primary Button Link</slot>
    </a>
  </template>
  <template v-else>
    <div type="submit" class="btn btn--primary">
      <slot name="title">Primary Button Submit</slot>
    </div>
  </template>
</template>

<script>
export default {
  props: {
    btnType: String
  },
  methods: {
    type(type) {
      if (type === "link") {
        return true;
      } else {
        return false;
      }
    }
  }
};
</script>

<style scoped lang="scss">
@use "./../sass/abstracts/abstracts" as abs;

.btn {
  display: block;
  text-align: center;
  cursor: pointer;
  white-space: pre;

  &--primary {
    color: abs.$vars-c-white;
    font-family: tlight;

    border-radius: 10rem;
    border: 0.2rem solid abs.$vars-c-darkblue;
    padding: 0.6rem 3rem;

    box-shadow: 0rem 0.1rem 0.1rem rgba(abs.$vars-c-black, 0.5),
      0.1rem 0.2rem 0.2rem rgba(abs.$vars-c-black, 0.5),
      0.2rem 0.3rem 0.3rem rgba(abs.$vars-c-black, 0.5);

    position: relative;

    display: flex;
    justify-content: center;
    align-items: center;

    @include abs.fns-respond(sptab) {
      border-color: abs.$vars-c-lightblue;

      color: rgba(abs.$vars-c-black, 1);
      font-weight: bold;
    }
    @include abs.fns-respond(lphone) {
      width: 100%;
      text-align: center;
    }

    &:hover {
      color: abs.$vars-c-darkblue;
      transition: all 0.3s ease-in-out;
      font-weight: bold;

      @include abs.fns-respond(sptab) {
        color: rgba(abs.$vars-c-lightblue, 1);
      }
    }

    &::before {
      content: "";
      display: block;

      height: 120%;
      position: absolute;
      top: 0;
      z-index: -5;
      background: rgba(abs.$vars-c-lightblue, 0);

      width: 0;
      right: 0;
      transform-origin: right;

      transition: all 0.3s ease-in-out;

      @include abs.fns-respond(sptab) {
        background: rgba(abs.$vars-c-black, 0);
      }
      @include abs.fns-respond(sptab) {
        transition: all 0.3s ease-in-out;
      }
    }
    &:hover::before {
      width: 120%;
      right: unset;
      left: 0;
      transform-origin: left;
      background: rgba(abs.$vars-c-lightblue, 1);

      @include abs.fns-respond(sptab) {
        background: rgba(abs.$vars-c-black, 0.9);
      }
    }
    &::after {
      content: "";
      display: block;

      height: 120%;
      width: 120%;

      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      z-index: -10;

      background: abs.$vars-c-darkblue;

      @include abs.fns-respond(sptab) {
        background: abs.$vars-c-lightblue;
      }
    }
  }
}
</style>
