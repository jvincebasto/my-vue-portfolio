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

    border-radius: 10rem;
    border: 0.2rem solid abs.$vars-c-darkblue;

    padding: 0.6rem 3rem;

    @include abs.fns-respond(sptab) {
      border-color: abs.$vars-c-lightblue;
      color: abs.$vars-c-lightblue;
    }
    @include abs.fns-respond(lphone) {
      width: 100%;
      margin-bottom: 1.5rem;
    }
  }
}
</style>
