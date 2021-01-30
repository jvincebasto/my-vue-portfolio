<script>
export default {
  methods: {
    addStyles(ref, items, unset) {
      if (items) {
        if (unset === false) {
          for (const item in items) {
            ref.style[item] = items[item];
          }
        } else {
          for (const item in items) {
            ref.style[item] = "";
          }
        }
      }
    },
    invokeStyles(obj, unset) {
      if (obj) {
        for (const el in obj) {
          if (el) {
            let ref;

            if (el === "link") {
              if (this.$refs[el]) {
                ref = this.$refs[el];
              } else {
                // ref = evt.children[3];
                ref = this.$refs.container.children[3];
              }
            } else {
              ref = this.$refs[el];
            }
            this.addStyles(ref, obj[el], unset);
          }
        }
      }
    }
  }
};
</script>

<!-- 
  
  //  Example Data to be passed on to Component 
  data() {

    const styleObj = {
      container: {
        borderRadius: "1rem"
      },
      bg: {},
      slide: {},
      border: {
        borderColor: "skyblue"
      },
      link: {
        padding: ".5rem 2rem",
        color: "skyblue"
      }
    };
    const all = {
      styleObj,
    };


    return {
      all,
      styleObj: all.styleObj,
    };
  },

-->

<!-- 
  
  //  Parent.vue File
  //  Example Component Prop Attribute
  

  // Pass as Data Property
    <template>
    <btn-component
      :btn-style="styleObj"
    >
    </btn-component>
    </template>


  // Pass as a Method
    <template>
    <btn-component
      :btn-style="styleObj()"
    >
    </btn-component>
    </template>

-->

<!-- 
  
  //  @Component.vue File
  //  Example Component Prop Recieved
  
  
  //  Import StyleMediaMatch.vue
  import StyleMediaMatch from "@/mixins/StyleMediaMatch.vue";

  
  //  Component.vue File Properties
  props: {
    btnStyle: Object,
  },
  data() {
    return {
      styleObj: this.btnStyle,
    };
  },
  mixins: [StyleMediaMatch],

-->
