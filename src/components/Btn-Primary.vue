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
    font-family: tthin;

    border-radius: 10rem;
    border: 0.2rem solid abs.$vars-c-darkblue;
    padding: 0.6rem 3rem;

    box-shadow: 0rem 0.1rem 0.1rem rgba(abs.$vars-c-black, 0.5),
      0.1rem 0.2rem 0.2rem rgba(abs.$vars-c-black, 0.5),
      0.2rem 0.3rem 0.3rem rgba(abs.$vars-c-black, 0.5);

    position: relative;

    &:hover {
      color: abs.$vars-c-darkblue;
      font-weight: bold;
      transition: all 1s 1s cubic-bezier(0.2, -0.5, 0.4, 1.75);
    }

    &::before {
      content: "";
      display: block;

      height: 100%;
      position: absolute;
      top: 0;
      z-index: -5;
      background: rgba(abs.$vars-c-lightblue, 0);

      width: 0;
      right: 0;
      transform-origin: right;

      transition: all 0.3s ease-in-out;
    }
    &:hover::before {
      width: 100%;
      right: unset;
      left: 0;
      transform-origin: left;
      background: rgba(abs.$vars-c-lightblue, 1);
    }
    &::after {
      content: "";
      display: block;

      height: 100%;
      width: 100%;

      position: absolute;
      top: 0;
      left: 0;
      z-index: -10;

      background: abs.$vars-c-darkblue;
    }

    @include abs.fns-respond(sptab) {
      border-color: abs.$vars-c-lightblue;
      background: abs.$vars-c-lightblue;
      color: abs.$vars-c-darkblue;
      font-family: tbody;
    }
    @include abs.fns-respond(lphone) {
      width: 100%;
      text-align: center;

      margin-bottom: 1.5rem;
    }
  }
}
</style>
