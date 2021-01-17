<template> 
	<Navbar />
  <router-view />
  <Footer />
</template>

<script>
// @ is an alias to /src
import Navbar from "@/components/Navbar.vue";
import Footer from "@/components/Footer.vue";

export default {
  components: {
    Navbar,
    Footer,
  }
};
</script>

<style lang="scss">

</style>
