<template>
  <section data-index="1" class="section section-about" id="about">
    <div class="section-margin">
      <hr />
      <div class="section-title">
        <h2>About Me</h2>
      </div>

      <div class="row">
        <div class="col col--left">
          <div class="category category-about family-background">
            <h3 class="category-title">Family Background</h3>
            <ul class="category-list category-list--about">
              <li>
                <svg class="category-icon">
                  <use xlink:href="resume-sprite.svg#man" />
                </svg>
                <p>
                  Father:
                  <span class="text-darkblue"> Pacifico B. Basto Jr.</span>
                </p>
              </li>
              <li>
                <svg class="category-icon">
                  <use xlink:href="resume-sprite.svg#desktop-1" />
                </svg>
                <p>
                  Occupation: <span class="text-darkblue"> Pastor</span>, Touch
                  Community Baptist Church, Bayombong, Nueva Vizcaya
                </p>
              </li>
              <li>
                <svg class="category-icon">
                  <use xlink:href="resume-sprite.svg#woman" />
                </svg>
                <p>
                  Mother:
                  <span class="text-darkblue"> Aryln S. Basto</span>
                </p>
              </li>
              <li>
                <svg class="category-icon">
                  <use xlink:href="resume-sprite.svg#desktop-1" />
                </svg>
                <p>
                  Occupation:
                  <span class="text-darkblue"> School Principal</span>, Aurora
                  Christian School, Bambang, Nueva Vizcaya
                </p>
              </li>
            </ul>
          </div>

          <div class="category category-about hobbies">
            <h3 class="category-title">Hobbies</h3>
            <ul class="category-list category-list--about">
              <li>
                <svg class="category-icon">
                  <use xlink:href="resume-sprite.svg#tv" />
                </svg>
                <p>
                  Watching <span class="text-darkblue"> Movies</span> and
                  <span class="text-darkblue"> Animes</span>
                </p>
              </li>
              <li>
                <svg class="category-icon">
                  <use xlink:href="resume-sprite.svg#drummer" />
                </svg>
                <p>
                  Playing <span class="text-darkblue"> Drums</span> and
                  Listening to
                  <span class="text-darkblue"> Music</span>
                </p>
              </li>
            </ul>
          </div>
        </div>

        <div class="col col--right">
          <div class="category category-about contacts">
            <h3 class="category-title">Contacts / Social Media</h3>
            <ul class="category-list category-list--about">
              <li>
                <svg class="category-icon">
                  <use xlink:href="resume-sprite.svg#house" />
                </svg>
                <p>
                  Address: #12 Zamora Street
                  <span class="text-darkblue"> Buag, Bambang</span>,
                  <span class="text-darkblue"> Nueva Vizcaya</span>
                </p>
              </li>
              <li>
                <svg class="category-icon">
                  <use xlink:href="resume-sprite.svg#email" />
                </svg>
                <p>
                  Email/
                  <span class="text-darkblue"> jvincentbasto</span>
                </p>
              </li>
              <li>
                <svg class="category-icon">
                  <use xlink:href="resume-sprite.svg#facebook" />
                </svg>
                <p>
                  Facebook/
                  <span class="text-darkblue"> jvince</span>
                </p>
              </li>
              <li>
                <svg class="category-icon">
                  <use xlink:href="resume-sprite.svg#github-1" />
                </svg>
                <p>
                  Github/
                  <span class="text-darkblue"> jvincebasto.github.io</span>
                </p>
              </li>
            </ul>
          </div>

          <div class="category category-about education">
            <h3 class="category-title">Education</h3>
            <ul class="category-list category-list--about">
              <li>
                <svg class="category-icon">
                  <use xlink:href="resume-sprite.svg#diploma-1" />
                </svg>
                <p>
                  College:
                  <span class="text-darkblue"> Saint Mary's University</span>
                  Bachelor Of Science in
                  <span class="text-darkblue"> Computer Engineering</span>
                  <span class="text-fade"> (2014 - 2019)</span>
                </p>
              </li>
              <li>
                <svg class="category-icon">
                  <use xlink:href="resume-sprite.svg#bag-1" />
                </svg>
                <p>
                  High School:
                  <span class="text-darkblue"> NVSU Highschool</span> Bambang,
                  Nueva Vizcaya
                  <span class="text-fade"> (2010 - 2014)</span>
                </p>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
// export default {
// };
</script>

<style scoped lang="scss">
@use "./../../sass/abstracts/abstracts" as abs;

.category {
  &-list--about {
    & li {
      margin-bottom: 1.5rem;
    }
    & li p {
      width: 100%;
    }
  }
  &-icon {
    height: 5rem;
    width: 5rem;
    margin-right: 3rem;

    fill: abs.$vars-c-primary;
    // background: crimson;

    @include abs.mxs-respond(mptab) {
      height: 8rem;
      width: 8rem;
      margin-right: 4rem;
    }
    @include abs.mxs-respond(lphone) {
      height: 6rem;
      width: 6rem;
      margin-right: 3rem;
    }
  }
}
</style>
