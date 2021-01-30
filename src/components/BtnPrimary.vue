<template>
  <template v-if="typeObj.type === 'link'">
    <div class="btn btn-container" ref="container">
      <div class="btn-bg" ref="bg"></div>
      <div class="btn-slide" ref="slide"></div>
      <div class="btn-border" ref="border"></div>
      <a :href="link(typeObj)" ref="link">
        <slot name="title">Primary Button - Link</slot>
      </a>
    </div>
  </template>
  <template v-else-if="typeObj.type === 'rlink'">
    <div class="btn btn-container" ref="container">
      <div class="btn-bg" ref="bg"></div>
      <div class="btn-slide" ref="slide"></div>
      <div class="btn-border" ref="border"></div>
      <router-link to="/" class="rlink">
        <slot name="title">Primary Button - Router Link</slot>
      </router-link>
    </div>
  </template>
  <template v-else>
    <div class="btn btn-container" ref="container">
      <div class="btn-bg" ref="bg"></div>
      <div class="btn-slide" ref="slide"></div>
      <div class="btn-border" ref="border"></div>
      <label for="submit" class="btn-label" ref="link">
        <slot name="title">Primary Button Submit</slot>
      </label>
      <input id="submit" type="submit" />
    </div>
  </template>
</template>

<script>
import btnTypes from "@/mixins/btns/btnType.vue";

export default {
  props: {
    btnType: Object
  },
  data() {
    return {
      typeObj: this.btnType
    };
  },
  mixins: [btnTypes]
};
</script>

<style scoped lang="scss">
@use "./../sass/abstracts/abstracts" as abs;

.btn {
  display: inline-block;
  cursor: pointer;

  &-container {
    border-radius: 10rem;

    position: relative;
    overflow: hidden;

    @include abs.mxs-respond(sptab) {
      height: 100%;
      width: 100%;
    }
  }

  & > * {
    display: block;
    height: 100%;
    width: 100%;

    position: absolute;
    top: 0;
    left: 0;

    border-radius: inherit;
    border: 0.2rem solid abs.$vars-c-primary;

    @include abs.mxs-respond(sptab) {
      height: inherit;
      width: inherit;
      border-color: abs.$vars-c-secondary;
    }
  }

  &-bg {
    background: abs.$vars-c-primary;
    border: none;

    @include abs.mxs-respond(sptab) {
      background: abs.$vars-c-secondary;
    }
  }
  &-border {
    // border-color: abs.$vars-c-black;
  }

  &-slide {
    background: rgba(abs.$vars-c-secondary, 0);
    border: none;
    width: 0;

    left: unset;
    right: 0;
    transform-origin: right;

    transition: all 0.3s ease-in-out;

    @include abs.mxs-respond(lphone) {
      transition-duration: 0.5s;
    }
  }
  &:hover &-slide {
    background: rgba(abs.$vars-c-secondary, 0.8);
    width: 100%;

    left: 0;
    transform-origin: left;

    @include abs.mxs-respond(sptab) {
      background: rgba(abs.$vars-c-black, 0.8);
    }
  }
  &:hover > a {
    color: abs.$vars-c-black;
    font-weight: bold;

    @include abs.mxs-respond(sptab) {
      color: rgba(abs.$vars-c-white, 0.8);
    }
  }

  & > a,
  &-label {
    cursor: inherit;
    font-family: tlight;
    font-size: 1.8rem;
    text-transform: uppercase;

    color: rgba(abs.$vars-c-white, 1);
    white-space: pre;

    border: none;
    padding: 1rem 3rem;

    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;

    @include abs.mxs-respond(sptab) {
      font-family: tthin;
      font-weight: bold;
    }
  }
  & #submit {
    height: 0;
    width: 0;
    background: blue;
  }
}
</style>
