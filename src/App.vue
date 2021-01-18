<template>
  <navbar />
  <router-view />
  <my-footer />
</template>

<script>
// @ is an alias to /src
import navbar from "@/components/Navbar.vue";
import myFooter from "@/components/Footer.vue";

export default {
  components: {
    navbar,
    myFooter
  }
};
</script>

<style lang="scss"></style>
