<template>
  <Hero />
  <About />
  <Skills />
</template>

<script>
import Hero from "./homepage/Hero.vue";
import About from "./homepage/About.vue";
import Skills from "./homepage/Skills.vue";

import Bp from "@/mixins/mediaMatch/MediaMatch.vue";
import styles from "@/sass/abstracts/_variables.scss";

export default {
  components: {
    Hero,
    About,
    Skills
  },
  mixins: [Bp],
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
  methods: {
    navCheck(entries) {
      const bubble = document.querySelector(".bubble");
      // const gradient = [orangered,royalblue,crimson];
      entries.forEach(entry => {
        const ids = entry.target.id;
        const links = document.querySelector(`[data-page=${ids}]`);

        const linkCoords = links.getBoundingClientRect();
        const props = {
          height: linkCoords.height,
          width: linkCoords.width,
          top: linkCoords.top,
          left: linkCoords.left
        };

        if (entry.isIntersecting) {
          for (const prop in props) {
            bubble.style.setProperty(prop, `${props[prop]}px`);
          }
        }
      });
    },
    observerFn() {
      const options = {
        threshold: 0
      };

      const observer = new IntersectionObserver(this.navCheck, options);
      return observer;
    },
    sectionList(...secArr) {
      if (secArr) {
        for (const secList in secArr) {
          if (secArr[secList].length > 0) {
            secArr[secList].forEach(section => {
              const observer = this.observerFn();
              observer.observe(section);
            });
          } else {
            const observer = this.observerFn();
            observer.observe(secArr[secList]);
          }
        }
      }
    },
    invokeObserver() {
      const sections = document.querySelectorAll("section");
      const footer = document.querySelector(".section-footer");
      if (sections) {
        this.sectionList(sections, footer);
      }
    }
  },
  mounted() {
    // if(this.mediaObj){
    //   const bp = this.breakpoint(this.mediaObj.width,this.mediaObj.minmax,this.mediaObj.unit);
    //   if(bp){
    //     this.invokeObserver();
    //     bp.addListener(this.invokeObserver);
    //   }
    // }
    this.invokeObserver();
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
    padding: 3vh 0;
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
