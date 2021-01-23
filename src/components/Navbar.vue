<template>
  <!--   <div id="nav">
    <router-link to="/#">About</router-link>
    <router-link to="/skills">Skills</router-link>
    <router-link to="/contacts">Contacts</router-link>
  </div>
 -->

  <!-- Navbar -->

  <nav class="nav section">
    <div class="nav-flex section-margin">
      <div class="nav-logo">
        <ul>
          <li>
            <btn-secondary
              :btnObj="btnlink('link', '#')"
              :btnBorder="'border-radius: 1rem'"
            >
              <template #title>John Vincent</template>

              <!--               <template #title>
                <template v-if="mediaMatch(1024)" @resize="mediaMatch(1024)">
                  <p>true</p>
                </template>
                <template v-else>
                  <p>false</p>
                </template>
              </template> -->
            </btn-secondary>
          </li>
        </ul>
      </div>

      <div class="nav-links">
        <ul>
          <li><a href="#about">About</a></li>
          <li><a href="#skills">Skills</a></li>
          <li><a href="#contacts">Contact</a></li>
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
import btnSecondary from "@/components/Btn-Secondary.vue";

// let x = window.matchMedia("(max-width: 768px)");

// mediaValidate(media = vw, obj = {}) {
//   if(media.matches) {
//     console.log("matched");
//     return true;
//   }
//   else {
//     console.log("No Media Query Matched")
//     return false;
//   }
// }

// x.addListener(mediaMatch);

// function mediaMatch(width = 1200) {
//   let vw = window.matchMedia(`(max-width: ${width}px)`);

//   function mediaValidate(media = vw) {
//     if(media.matches) {
//       console.log("matched");
//       return true;
//     }
//     else {
//       console.log("No Media Query Matched")
//       return false;
//     }
//   }

//   vw.addListener(mediaValidate);
// }

export default {
  components: {
    btnSecondary
  },
  methods: {
    btnlink(type = "link", link = "#") {
      const btnObj = {
        type,
        link
      };

      return btnObj;
    },
    mediaMatch(width = 1200) {
      const filterWidth = parseFloat(width);
      let vw = window.matchMedia(`(max-width: ${filterWidth}px)`);

      function mediaValidate(media = vw) {
        if (media.matches) {
          console.log("matched");
          return true;
        } else {
          console.log("No Media Query Matched");
          return false;
        }
      }

      const bool = mediaValidate();
      vw.addListener(mediaValidate);

      console.log(bool);
      return bool;
    }
  }
};
</script>

<style scoped lang="scss">
@use "./../sass/abstracts/abstracts" as abs;

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

  @include abs.fns-respond(cphone) {
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

    @include abs.fns-respond(cphone) {
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
      margin-right: 3rem;

      @include abs.fns-respond(cphone) {
        // margin-right: 1.5rem;
      }

      & a::before {
        content: "";
        display: block;

        height: 0.2rem;
        position: absolute;
        bottom: 0;
        z-index: -5;
        background: rgba(abs.$vars-c-lightblue, 0);

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
        background: rgba(abs.$vars-c-lightblue, 1);
      }

      & a {
        display: block;
        height: 100%;
        width: 100%;

        text-align: center;
        white-space: pre;
        color: abs.$vars-c-white;

        position: relative;

        &:hover {
          color: abs.$vars-c-lightblue;
          font-weight: bold;
        }

        @include abs.fns-respond(cphone) {
          // padding: .5rem 2rem;
          // border-radius: 10rem;
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

    @include abs.fns-respond(cphone) {
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

    @include abs.fns-respond(sptab) {
      display: unset;
    }
  }

  &-up--icon {
    height: inherit;
    width: inherit;
    fill: abs.$vars-c-lightblue;
  }
}
</style>
