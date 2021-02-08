<template>
  <!--   <div id="nav">
    <router-link to="/#">About</router-link>
    <router-link to="/skills">Skills</router-link>
    <router-link to="/contacts">Contacts</router-link>
  </div>
 -->

  <!-- Navbar -->

  <nav class="nav section" ref="sectNav">
    <div class="nav-flex section-margin">
      <div class="nav-logo">
        <ul>
          <li ref="nlinkHero">
            <btn-secondary
              data-page="hero"
              :btn-type="linkObj('link', '#')"
              :btn-bp="bpObj(mediaObj.width, mediaObj.minmax, mediaObj.unit)"
              :btn-multi-obj="fnTypes"
            >
              <template #title>John Vincent</template>
            </btn-secondary>
          </li>
        </ul>
      </div>

      <div class="nav-links">
        <ul>
          <li ref="nlinkAbout" data-page="about"><a href="#about">About</a></li>
          <li ref="nlinkSkills" data-page="skills">
            <a href="#skills">Skills</a>
          </li>
          <li ref="nlinkContacts" data-page="contacts">
            <a href="#contacts">Contact</a>
          </li>
          <li ref="bubbleSlider" class="bubble"></li>
          <!-- <li><router-link to="/">list</router-link></li> -->
        </ul>
      </div>
    </div>
  </nav>

  <div>
    <a class="btn-up" href="#">
      <svg class="btn-up--icon">
        <use xlink:href="resume-sprite.svg#arrow-up-2" />
      </svg>
    </a>
  </div>
</template>

<script>
import btnSecondary from "@/components/BtnSecondary.vue";
import styles from "@/sass/abstracts/_variables.scss";

export default {
  components: {
    btnSecondary
  },
  data() {
    const mediaObj = {
      width: styles.mqSptab,
      minmax: "min",
      unit: "em"
    };

    const styleObj = {
      container: {
        borderRadius: "1rem"
      },
      bg: {},
      slide: {},
      border: {
        borderColor: styles.cSecondary
      },
      link: {
        padding: ".5rem 2rem",
        color: styles.cSecondary
      }
    };

    const container = {
      evt: "container",
      events: {
        onmouseover: {
          slide: {
            background: styles.cPrimary
          }
        },
        onmouseleave: {
          link: {
            color: styles.cSecondary
          }
        }
      }
    };

    const fnTypes = {
      styles: {
        mqStyles: styleObj
      },
      events: {
        containerEvent: container
      }
    };

    const all = {
      mediaObj,
      fnTypes
    };

    return {
      all,
      mediaObj: all.mediaObj,
      fnTypes: all.fnTypes
    };
  },
  methods: {
    linkObj(type = "link", link = "#") {
      const obj = {
        type,
        link
      };
      return obj;
    },
    bpObj(width, minmax, unit) {
      const obj = {
        width,
        minmax,
        unit
      };
      return obj;
    }
  }
  // created() {
  //   console.log('navbar created');
  // },
  // mounted() {
  //   console.log('navbar mounted');
  // }
};
</script>

<style scoped lang="scss">
@use "./../sass/abstracts/abstracts" as abs;

.bubble {
  position: absolute;
  z-index: -100;
  top: -25%;
  background: rgba(abs.$vars-c-secondary, 0.2);

  transition: all 0.4s ease-in-out;
}

/* ~~~~~ Navbar ~~~~~ */

.nav {
  min-height: unset;
  height: 7rem;
  width: 100%;

  display: flex;
  align-items: center;

  position: fixed;
  top: 0;
  left: 0;
  z-index: 5000;

  background: rgba(abs.$vars-c-black, 0.6);

  @include abs.mxs-respond(cphone) {
    background: linear-gradient(to bottom, abs.$vars-c-black 60%, transparent),
      linear-gradient(to bottom, abs.$vars-c-black 60%, transparent 99%),
      linear-gradient(to bottom, abs.$vars-c-black 60%, transparent 98%),
      linear-gradient(to bottom, abs.$vars-c-black 60%, transparent 97%),
      linear-gradient(to bottom, abs.$vars-c-black 60%, transparent 96%);
  }

  &-flex {
    display: flex;
    justify-content: space-between;
    align-items: center;

    @include abs.mxs-respond(cphone) {
      // justify-content: flex-end;
    }
  }

  & ul li a {
    font-family: tthin;
  }

  &-links ul {
    display: flex;

    // background: green;

    & li {
      margin-right: 1.5rem;
      border-radius: 1rem;

      @include abs.mxs-respond(cphone) {
        // margin-right: 1.5rem;
      }

      & a::before {
        content: "";
        display: block;

        height: 0.2rem;
        position: absolute;
        bottom: 0;
        z-index: -5;
        background: rgba(abs.$vars-c-secondary, 0);

        width: 0;
        right: 0;
        transform-origin: right;

        transition: all 0.3s ease-in-out;
      }
      &:hover a::before {
        width: 100%;
        right: unset;
        left: 0;
        transform-origin: left;
        background: rgba(abs.$vars-c-secondary, 1);
      }

      & a {
        display: block;
        height: 100%;
        width: 100%;

        text-align: center;
        white-space: pre;
        color: abs.$vars-c-white;

        position: relative;
        padding: 0.2rem 0.8rem;

        &:hover {
          color: abs.$vars-c-secondary;
          font-weight: bold;
        }

        @include abs.mxs-respond(cphone) {
          // padding: .5rem 2rem;
          // border-radius: 1rem;
          // background: rgba(abs.$vars-c-black,.1);
        }
      }
    }
    & li:last-child {
      margin-right: 0;
    }
  }

  &-logo {
    display: flex;
    align-items: center;

    @include abs.mxs-respond(cphone) {
      display: none;
    }
  }
  &-logo ul li {
    border-radius: 1rem;

    & > * {
      display: block;
    }
  }
}

.btn {
  &-up {
    height: 4rem;
    width: 4rem;

    border-radius: 10rem;

    position: fixed;
    bottom: 8vh;
    right: 5vh;
    z-index: 5000;

    display: none;

    @include abs.mxs-respond(sptab) {
      display: unset;
    }
  }

  &-up--icon {
    height: inherit;
    width: inherit;
    fill: abs.$vars-c-secondary;
  }
}
</style>
