<script>
export default {
  methods: {
    // type(obj,btnType = "link") {
    //   if (obj) {
    //     if (obj.type === btnType) {
    //       console.log("link");
    //       return true;
    //     }
    //     else if (obj.type === btnType) {
    //       console.log("rlink");
    //       return true;
    //     }
    //     else {
    //       console.log("sumbit");
    //       return false;
    //     }
    //   }
    // },
    link(obj) {
      if (obj) {
        if (!obj.link) {
          return "#";
        } else {
          return obj.link;
        }
      }
    }
  }
};
</script>
