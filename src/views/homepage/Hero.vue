<template>
  <section
    data-index="0"
    class="section section-hero section-hero--height"
    id="hero"
  >
    <div class="section-margin">
      <div class="headline headline-block">
        <h1 class="headline-primary">
          <span class="headline-primary">I’m</span> John <br />
          <span class="headline-primary headline-primary--nickname">Vince</span
          >nt Basto
        </h1>
        <span class="headline-secondary text-fade">
          A Web Developer
        </span>

        <p>
          Hi there! How are you doing this time of pandemic,
          <span class="text-darkblue"> I hope you’re doing fine and well</span>.
          I’m a graduate of
          <span class="text-darkblue"> Computer Engineering</span>
          who likes
          <span class="text-darkblue"> Web Development</span>. What can I do for
          you?
        </p>

        <div class="btn-headline">
          <ul>
            <li>
              <btn-primary :btn-type="linkObj('link', '#about')">
                <template #title>About Me</template>
              </btn-primary>
            </li>
            <li>
              <btn-secondary :btn-type="linkObj('link', '#contacts')">
                <template #title>Contact</template>
              </btn-secondary>
            </li>
          </ul>
        </div>
      </div>
    </div>

    <div class="section-bg section-hero--height">
      <div class="section-bg section-bg--color">&nbsp;</div>
      <div class="section-bg" id="bg_whiteboxes">&nbsp;</div>
      <div
        class="section-bg__gradient
			section-bg__gradient-left"
      >
        &nbsp;
      </div>
    </div>

    <div class="section-hero--height profile">
      <img
        id="profile_picture"
        src="@/assets/imgs/profile.webp"
        alt="profile-picture"
      />
    </div>

    <div
      class="section-bg__overlay 
		section-bg__overlay--1"
    >
      &nbsp;
    </div>
    <div
      class="section-bg__overlay 
		section-bg__overlay--2"
    >
      &nbsp;
    </div>

    <div
      class="section-bg__gradient 
		section-bg__gradient-bottom"
    >
      &nbsp;
    </div>
    <div
      class="section-bg__gradient 
		section-bg__gradient-top"
    >
      &nbsp;
    </div>
  </section>
</template>

<script>
import btnPrimary from "@/components/BtnPrimary.vue";
import btnSecondary from "@/components/BtnSecondary.vue";

export default {
  components: {
    btnPrimary,
    btnSecondary
  },
  methods: {
    linkObj(type = "link", link = "#") {
      const obj = {
        type,
        link
      };
      return obj;
    }
  }
};
</script>

<style scoped lang="scss">
@use "./../../sass/abstracts/abstracts" as abs;

.section {
  &-hero {
    width: 100%;
    padding: 14rem 0 7rem;
    display: flex;
    align-items: center;

    position: relative;
    // background: blue;

    @include abs.mxs-respond(sptab) {
      background: linear-gradient(
        135deg,
        abs.$vars-c-secondary,
        abs.$vars-c-primary 40%
      );
    }
    @include abs.mxs-respond(lphone) {
      background: linear-gradient(
        135deg,
        abs.$vars-c-secondary,
        abs.$vars-c-primary 35%
      );
    }

    &--height {
      height: 80rem;

      @include abs.mxs-respond(sptab) {
        height: 200rem;
        padding-bottom: 14rem;
      }
    }

    & > * {
      display: flex;
      align-items: center;

      @include abs.mxs-respond(sptab) {
        display: flex;
        align-items: center;

        color: abs.$vars-c-white;
      }
    }
  }

  &-margin {
    height: 100%;
    position: relative;
    z-index: 100;
  }
}

.headline {
  &-block {
    width: 100%;

    @include abs.mxs-respond(sptab) {
      margin-top: 50rem;
    }
    @include abs.mxs-respond(lphone) {
      margin-top: 80rem;
    }
  }

  &-primary {
    display: block;
    font-family: hbody;
    text-transform: lowercase;
    color: rgba(abs.$vars-c-black, 0.8);

    font-size: 7.8rem;
    letter-spacing: -0.3rem;
    line-height: 0.9;

    margin-bottom: 0.3rem;

    @include abs.mxs-respond(mptab) {
    }
    @include abs.mxs-respond(sptab) {
      text-transform: capitalize;
      font-size: 5.8rem;
      color: abs.$vars-c-secondary;
    }

    & > span {
      display: inline-block;
      text-transform: capitalize;
      // font-family: hthin;
    }
    & > span:first-child {
      color: abs.$vars-c-primary;

      @include abs.mxs-respond(sptab) {
        color: rgba(abs.$vars-c-white, 0.8);
      }
    }
    &--nickname {
      color: abs.$vars-c-primary;

      @include abs.mxs-respond(sptab) {
        color: rgba(abs.$vars-c-white, 0.8);
      }
    }
  }

  &-secondary {
    display: block;
    text-transform: uppercase;
    letter-spacing: 1.2rem;

    margin-bottom: 3rem;

    @include abs.mxs-respond(mptab) {
      letter-spacing: 0.8rem;
    }
    @include abs.mxs-respond(sptab) {
      letter-spacing: 0.6rem;
      font-family: tthin;
    }
  }

  & > p {
    max-width: 45ch;
    margin-bottom: 3rem;

    @include abs.mxs-respond(mptab) {
      max-width: 42ch;
    }
    @include abs.mxs-respond(sptab) {
      max-width: 58ch;
      font-family: tthin;
    }
    @include abs.mxs-respond(cphone) {
      max-width: 50ch;
    }
    @include abs.mxs-respond(lphone) {
      max-width: 32ch;
      margin-bottom: 6rem;
    }
    @include abs.mxs-respond(sphone) {
      max-width: 25ch;
    }
  }
  & p span {
    text-transform: capitalize;

    @include abs.mxs-respond(sptab) {
      color: abs.$vars-c-secondary !important;
    }
  }
}

.btn {
  &-headline ul {
    width: 100%;
    display: flex;

    // background: green;

    @include abs.mxs-respond(lphone) {
      width: 100%;
      flex: 1 1 auto;
      flex-wrap: wrap;
    }
  }
  &-headline ul li {
    margin-right: 3rem;
    border-radius: 10rem;

    @include abs.mxs-respond(lphone) {
      margin-right: 0;
      width: 100%;

      display: flex;
      justify-content: center;
      align-items: center;
      margin-bottom: 1.5rem;
    }
  }
  &-headline ul li:last-child {
    margin-right: 0;
    margin-bottom: 0;
  }
}

.section-bg {
  width: 100%;
  max-width: 50%;

  position: absolute;
  top: 0;
  right: 0;
  z-index: -10;

  clip-path: polygon(10rem 0, 100% 0, 100% 100%, 0 100%);

  & * {
    max-width: unset;
  }

  @include abs.mxs-respond(sptab) {
    max-width: unset;
  }

  &--color {
    height: inherit;
    width: 100%;
    background: linear-gradient(
      135deg,
      abs.$vars-c-primary,
      abs.$vars-c-secondary
    );

    @include abs.mxs-respond(sptab) {
      display: none;
    }
  }

  &__gradient {
    height: inherit;
    width: 100%;

    position: absolute;
    top: 0;
    left: 0;

    &-left {
      height: 120%;
      width: 10rem;

      right: unset;
      left: 4rem;
      top: -10%;

      @include abs.mxs-respond(sptab) {
        display: none;
      }

      background: linear-gradient(to right, abs.$vars-c-white, transparent),
        linear-gradient(to right, abs.$vars-c-white, transparent 98%),
        linear-gradient(to right, abs.$vars-c-white, transparent 96%),
        linear-gradient(to right, abs.$vars-c-white, transparent 94%),
        linear-gradient(to right, abs.$vars-c-white, transparent 92%);

      transform: rotateZ(7deg);
    }

    &-top {
      z-index: 10;

      height: 7.5rem;
      display: none;

      background: linear-gradient(to bottom, abs.$vars-c-black, transparent),
        linear-gradient(to bottom, abs.$vars-c-black, transparent 99%),
        linear-gradient(to bottom, abs.$vars-c-black, transparent 98%),
        linear-gradient(to bottom, abs.$vars-c-black, transparent 97%),
        linear-gradient(to bottom, abs.$vars-c-black, transparent 96%);

      @include abs.mxs-respond(cphone) {
        display: unset;
      }
    }

    &-bottom {
      z-index: 30;

      height: 5%;
      top: unset;
      bottom: 0;

      background: linear-gradient(to top, abs.$vars-c-white, transparent),
        linear-gradient(to top, abs.$vars-c-white, transparent 90%),
        linear-gradient(to top, abs.$vars-c-white, transparent 80%),
        linear-gradient(to top, abs.$vars-c-white, transparent 70%),
        linear-gradient(to top, abs.$vars-c-white, transparent 60%);
    }
  }

  &__overlay {
    height: inherit;
    width: 100%;

    position: absolute;
    bottom: 0;
    left: 0;
    z-index: 20;

    display: none;

    @include abs.mxs-respond(sptab) {
      display: unset;
    }

    &--1 {
      background: rgba(abs.$vars-c-black, 0.2);
    }
    &--2 {
      background: linear-gradient(
          to top,
          transparent 50%,
          abs.$vars-c-black 50%,
          transparent
        ),
        linear-gradient(
          to top,
          transparent 50%,
          abs.$vars-c-black 50%,
          transparent 95%
        ),
        linear-gradient(
          to top,
          transparent 50%,
          abs.$vars-c-black 50%,
          transparent 90%
        ),
        linear-gradient(
          to top,
          transparent 50%,
          abs.$vars-c-black 50%,
          transparent 85%
        ),
        linear-gradient(
          to top,
          transparent 50%,
          abs.$vars-c-black 50%,
          transparent 80%
        ),
        linear-gradient(
          to bottom,
          transparent 50%,
          abs.$vars-c-black 50%,
          abs.$vars-c-black 90%,
          transparent
        ),
        linear-gradient(
          to bottom,
          transparent 50%,
          abs.$vars-c-black 50%,
          abs.$vars-c-black 90%,
          transparent 99%
        ),
        linear-gradient(
          to bottom,
          transparent 50%,
          abs.$vars-c-black 50%,
          abs.$vars-c-black 90%,
          transparent 98%
        ),
        linear-gradient(
          to bottom,
          transparent 50%,
          abs.$vars-c-black 50%,
          abs.$vars-c-black 90%,
          transparent 97%
        ),
        linear-gradient(
          to bottom,
          transparent 50%,
          abs.$vars-c-black 50%,
          abs.$vars-c-black 90%,
          transparent 96%
        );
      height: 68%;
    }
  }
}

.profile {
  width: 100%;

  position: absolute;
  top: 0;
  right: 0;
  z-index: 15;

  overflow: hidden;
}
#profile_picture {
  width: 88rem;
  position: absolute;
  top: -5%;
  right: -10%;

  filter: drop-shadow(0.6rem 0.6rem 0.6rem rgba(abs.$vars-c-black, 0.3))
    drop-shadow(0.7rem 0.7rem 0.7rem rgba(abs.$vars-c-black, 0.3))
    drop-shadow(0.8rem 0.8rem 0.8rem rgba(abs.$vars-c-black, 0.3));

  @include abs.mxs-respond(mlaptop) {
    right: -15%;
  }
  @include abs.mxs-respond(slaptop) {
    right: -25%;
  }
  @include abs.mxs-respond(mptab) {
    right: -32%;
  }
  @include abs.mxs-respond(sptab) {
    top: 5%;
    width: 100rem;
    right: unset;
    left: 50%;
    transform: translateX(-40%);
  }
  @include abs.mxs-respond(cphone) {
    // filter: blur(2rem);
  }
  @include abs.mxs-respond(lphone) {
    width: 85rem;
    transform: translateX(-45%);
  }
}
#bg_whiteboxes {
  height: 100%;
  width: 100%;

  background-image: url(./../../assets/imgs/bg-whitebox.png);
  background-size: cover;
  background-repeat: no-repeat;

  // display: none;
}
</style>
