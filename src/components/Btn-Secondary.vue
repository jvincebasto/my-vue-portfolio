<template>
  <template v-if="type(btnType)">
    <a class="btn btn--secondary">
      <slot name="title">Secondary Button Link</slot>
    </a>
  </template>
  <template v-else>
    <div type="submit" class="btn btn--secondary">
      <slot name="title">Secondary Button Submit</slot>
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

  &--secondary {
    background: transparent;
    color: abs.$vars-c-darkblue;
    font-family: tlight;
    font-weight: bold;

    border-radius: 10rem;
    border: 0.2rem solid abs.$vars-c-darkblue;
    padding: 0.6rem 3rem;

    position: relative;

    @include abs.fns-respond(sptab) {
      color: abs.$vars-c-darkblue;
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

      @include abs.fns-respond(sptab) {
        background: rgba(abs.$vars-c-lightblue, 0);
      }
    }
    &:hover::before {
      width: 100%;
      right: unset;
      left: 0;
      transform-origin: left;
      background: rgba(abs.$vars-c-lightblue, 1);

      @include abs.fns-respond(sptab) {
        background: rgba(abs.$vars-c-lightblue, 0.1);
      }
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

      background: transparent;
    }

    @include abs.fns-respond(sptab) {
      border-color: abs.$vars-c-lightblue;
      color: abs.$vars-c-lightblue;
    }
    @include abs.fns-respond(lphone) {
      width: 100%;
    }
  }
}
</style>
