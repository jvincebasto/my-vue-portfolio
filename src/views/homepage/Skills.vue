<template>
  <section
    data-section="skills"
    class="section section-skills"
    id="skills"
    ref="sectSkills"
  >
    <div class="section-margin">
      <hr />
      <div class="section-title">
        <h2>Skills</h2>
      </div>

      <div class="row">
        <div class="col col--left">
          <div
            class="category category-skills category-skills--left interpersonal"
          >
            <h3 class="category-title">Interpersonal</h3>
            <ul class="category-list category-list--skills">
              <li>
                <span>Problem Solving</span>
                <btn-radios class="btn-radio--4"></btn-radios>
              </li>
              <li>
                <span>Time Management</span>
                <btn-radios class="btn-radio--3"></btn-radios>
              </li>
              <li>
                <span
                  >Attention to<span class="text-darkblue"> Detail</span></span
                >
                <btn-radios class="btn-radio--4"></btn-radios>
              </li>
              <li>
                <span>Multi Tasking</span>
                <btn-radios class="btn-radio--3"></btn-radios>
              </li>
              <li>
                <span>Organized</span>
                <btn-radios class="btn-radio--4"></btn-radios>
              </li>
            </ul>
          </div>

          <div
            class="category category-skills category-skills--left technical-skills"
          >
            <h3 class="category-title">Technical Skills</h3>
            <ul class="category-list category-list--skills">
              <li>
                <span>Microsoft Skills</span>
                <btn-radios class="btn-radio--4"></btn-radios>
              </li>
              <li>
                <span>Electronic Cicuitry</span>
                <btn-radios class="btn-radio--3"></btn-radios>
              </li>
              <li>
                <span>Web Development</span>
                <btn-radios class="btn-radio--4"></btn-radios>
              </li>
            </ul>
          </div>
        </div>

        <div class="col col--right">
          <div
            class="category category-skills category-skills--right web-languages"
          >
            <h3 class="category-title">Web Languages</h3>
            <ul class="category-list category-list--skills">
              <li>
                <span>CSS</span>
                <pg-bar :pgBarFill="pbPercent(80)"></pg-bar>
              </li>
              <li>
                <span>JavaScript</span>
                <pg-bar :pgBarFill="pbPercent(78)"></pg-bar>
              </li>
              <li>
                <span>PHP</span>
                <pg-bar :pgBarFill="pbPercent(68)"></pg-bar>
              </li>
              <li>
                <span>SQL</span>
                <pg-bar :pgBarFill="pbPercent(75)"></pg-bar>
              </li>
              <li>
                <span>Laravel</span>
                <pg-bar :pgBarFill="pbPercent(65)"></pg-bar>
              </li>
              <li>
                <span>Vue Js</span>
                <pg-bar :pgBarFill="pbPercent(75)"></pg-bar>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import btnRadios from "@/components/BtnRadios.vue";
import pgBar from "@/components/ProgressBar.vue";

export default {
  components: {
    btnRadios,
    pgBar
  },
  methods: {
    pbPercent(percent = 55) {
      let fillWidth = ` width: ${parseFloat(percent)}% `;

      return fillWidth;
    }
  }
};
</script>

<style lang="scss">
@use "./../../sass/abstracts/abstracts" as abs;

.category {
  &-list {
    // background: green;
  }
  &-list--skills {
    & li {
      @include abs.mxs-respond(mphone) {
        flex-wrap: wrap;
        margin-bottom: 1.5rem;
      }
    }
    & li > span {
      margin-right: auto;
      min-width: 50%;

      @include abs.mxs-respond(mphone) {
        margin-right: unset;
        min-width: 100%;
        margin-bottom: 0.5rem;
      }
    }
    & li > * {
      // background: crimson;
    }
  }
}
</style>
