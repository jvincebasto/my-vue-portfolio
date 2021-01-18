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
    background: abs.$vars-c-darkblue;
    color: abs.$vars-c-white;
    font-family: tthin;

    border-radius: 10rem;
    border: 0.2rem solid abs.$vars-c-darkblue;
    padding: 0.6rem 3rem;

    filter: drop-shadow(0rem 0.2rem 0.2rem rgba(abs.$vars-c-black, 0.6));

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
