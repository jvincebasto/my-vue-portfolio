<template>
  <footer data-index="3" class="section section-footer" id="contacts">
    <div class="section-margin">
      <div class="section-title">
        <h2>Contacts</h2>
      </div>

      <div class="category category-contacts">
        <ul class="category-list category-list--contacts">
          <li>
            <p>
              Email: <span class="text-fade">jvincentbasto@gmail.com </span>
            </p>
          </li>
          <li>
            <p>Facebook/ <span class="text-fade">Jvince </span></p>
          </li>
          <li>
            <p>Github/ <span class="text-fade">Jvincebasto.github.io </span></p>
          </li>
        </ul>
      </div>

      <div class="footer-logo">
        <img
          id="footer-logo--bg"
          src="@/assets/imgs/logo-left-white.png"
          alt="footer-logo--bg"
        />
      </div>
    </div>
  </footer>
</template>

<script>
// export default {
// };
</script>

<style scoped lang="scss">
@use "./../sass/abstracts/abstracts" as abs;

.section {
  &-footer {
    min-height: 10rem;

    background: rgba(abs.$vars-c-black, 0.9);

    position: relative;
    overflow: hidden;
  }
  &-title > * {
    font-family: hthin;
  }
  &-footer * {
    color: abs.$vars-c-white;
  }
}

.category {
  &-list li * {
    font-family: tthin;
  }

  &-contacts {
    margin-bottom: 0rem;
  }
}

.footer-logo {
  height: 100%;
  width: 100%;

  position: absolute;
  top: 0;
  right: 0;
}
#footer-logo--bg {
  width: 72rem;

  position: absolute;
  top: -30%;
  right: -20%;

  opacity: 0.3;

  @include abs.mxs-respond(mlaptop) {
    right: -25%;
  }
  @include abs.mxs-respond(mptab) {
    right: -35%;
  }
  @include abs.mxs-respond(sptab) {
    opacity: 0.2;
    right: -40%;
  }
  @include abs.mxs-respond(cphone) {
    right: -55%;
  }
  @include abs.mxs-respond(lphone) {
    right: -75%;
  }
  @include abs.mxs-respond(mphone) {
    right: -85%;
  }
  @include abs.mxs-respond(sphone) {
    right: -100%;
  }
}
</style>
