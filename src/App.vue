<template>
  <navbar ref="compNav" />
  <router-view :refs-obj="refsObj" />
  <my-footer ref="compFooter" />
</template>

<script>
// @ is an alias to /src
import navbar from "@/components/Navbar.vue";
import myFooter from "@/components/Footer.vue";

import getRefs from "@/mixins/getRefs/GetRefs.vue";

export default {
  components: {
    navbar,
    myFooter
  },
  data() {
    return {
      refsObj: {
        navLinks: {},
        sections: {}
      }
    };
  },
  mixins: [getRefs],
  created() {
    // console.log('App Created');
  },
  mounted() {
    this.collectRefs(this.refsObj, this.$refs, this.appCompRefs);
  }
};
</script>

<style lang="scss"></style>
