<template>
  <template v-if="btnType(btnObj)">
    <div class="btn btn-container" :style="$attrs.btnBorder">
      <div class="btn-bg"></div>
      <div class="btn-slide"></div>
      <div class="btn-border"></div>
      <a :href="btnLink(btnObj)">
        <slot name="title">Primary Button - Link</slot>
      </a>
    </div>
  </template>
  <template v-else>
    <div class="btn btn-container" :style="$attrs.btnBorder">
      <div class="btn-bg"></div>
      <div class="btn-slide"></div>
      <div class="btn-border"></div>
      <label for="submit" class="btn-label">
        <slot name="title">Primary Button Submit</slot>
      </label>
      <input id="submit" type="submit" />
    </div>
  </template>
</template>

<script>
// let x = window.matchMedia("(max-width: 1024px)");

// function mediaValidate(media) {
//   if(media.matches) {
//     console.log("matched");
//     return true;
//   }
//   else {
//     console.log("No Media Query Matched")
//     return false;
//   }
// }

// x.addListener(mediaValidate);

export default {
  props: {
    btnObj: Object
  },
  methods: {
    btnType(obj) {
      if (obj.type === "link") {
        return true;
      } else {
        return false;
      }
    },
    btnLink(obj) {
      if (!obj.link) {
        return "#";
      } else {
        return obj.link;
      }
    }
  }
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

    @include abs.fns-respond(sptab) {
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
    border: 0.2rem solid abs.$vars-c-darkblue;

    @include abs.fns-respond(sptab) {
      height: inherit;
      width: inherit;
      border-color: abs.$vars-c-lightblue;
    }
  }

  &-bg {
    background: abs.$vars-c-darkblue;
    border: none;

    @include abs.fns-respond(sptab) {
      background: abs.$vars-c-lightblue;
    }
  }
  &-border {
    // border-color: abs.$vars-c-black;
  }

  &-slide {
    background: rgba(abs.$vars-c-lightblue, 0);
    border: none;
    width: 0;

    left: unset;
    right: 0;
    transform-origin: right;

    transition: all 0.3s ease-in-out;

    @include abs.fns-respond(lphone) {
      transition-duration: 0.5s;
    }
  }
  &:hover &-slide {
    background: rgba(abs.$vars-c-lightblue, 0.8);
    width: 100%;

    left: 0;
    transform-origin: left;

    @include abs.fns-respond(sptab) {
      background: rgba(abs.$vars-c-black, 0.8);
    }
  }
  &:hover > a {
    color: abs.$vars-c-black;
    font-weight: bold;

    @include abs.fns-respond(sptab) {
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

    @include abs.fns-respond(sptab) {
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
