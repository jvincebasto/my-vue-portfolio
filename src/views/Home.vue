<template>
  <Hero ref="compHero" />
  <About ref="compAbout" />
  <Skills ref="compSkills" />
</template>

<script>
import Hero from "./homepage/Hero.vue";
import About from "./homepage/About.vue";
import Skills from "./homepage/Skills.vue";

import Bp from "@/mixins/mediaMatch/MediaMatch.vue";
import getRefs from "@/mixins/getRefs/GetRefs.vue";
import intersectObs from "@/mixins/intersectionObservers/intersectObs.vue";
import styles from "@/sass/abstracts/_variables.scss";

export default {
  props: {
    refsObj: Object
  },
  components: {
    Hero,
    About,
    Skills
  },
  mixins: [Bp, getRefs, intersectObs],
  data() {
    const mediaObj = {
      width: styles.mqSlaptop,
      minmax: "min",
      unit: "em"
    };

    return {
      mediaObj
    };
  },
  created() {
    // console.log('home Created');
  },
  mounted() {
    // console.log('home mounted');

    const bp = this.breakpoint(
      this.mediaObj.width,
      this.mediaObj.minmax,
      this.mediaObj.unit
    );

    this.collectRefs(this.refsObj, this.$refs, this.homeCompRefs);
    if (bp.matches) {
      // console.log("Added Observer");

      const options = this.observerOpt();
      this.invokeObserver(options, this.bubbleSliderFn, this.refsObj, false);
    } else {
      // console.log("Removed Observer");

      const options = this.observerOpt(0.4);
      this.invokeObserver(options, this.bubbleSliderFn, this.refsObj, true);
    }
  }
};
</script>

<style lang="scss">
@use "./../sass/abstracts/abstracts" as abs;

.section {
  height: auto;
  min-height: 25vh;
  width: auto;
  max-width: 144rem;

  overflow: hidden;

  &-about,
  &-skills,
  &-footer {
    padding: 7rem 0;

    // background: yellow;
  }

  &-margin {
    height: auto;
    width: 100%;
    max-width: 85%;
    margin: auto;

    @include abs.mxs-respond(mlaptop) {
      max-width: 90%;
    }

    // background: orange;
  }

  &-title {
    padding: 3rem 0;
    margin-bottom: 3rem;

    // background: green;
  }
  &-title > * {
    font-family: hthin;
    text-transform: uppercase;
    letter-spacing: 0.9rem;
    color: rgba(abs.$vars-c-black, 0.8);
  }
}

.row {
  height: auto;
  width: auto;

  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;

  // background: green;
}
.col {
  flex: 1 1 auto;
  max-width: 45%;
  padding-right: 2%;

  // background: crimson;

  @include abs.mxs-respond(mptab) {
    min-width: 100%;
    padding: 0;
  }
}

.category {
  margin-bottom: 6rem;

  // background: blue;

  &:last-child {
    // margin-bottom: 0;
  }

  &-title {
    text-transform: uppercase;
    font-family: tthin;
    letter-spacing: 0.3rem;
    color: abs.$vars-c-primary;

    margin-bottom: 1.5rem;
  }

  &-list {
    & li {
      display: flex;
      align-items: center;
    }
    & li p span {
      // white-space: unset;
    }
  }
}
</style>
