<script>
export default {
  methods: {
    breakpoint(width = 1024, minmax = "max", unit = "px") {
      const widthFilter = parseFloat(width);
      const bp = window.matchMedia(`(${minmax}-width: ${widthFilter}${unit})`);
      return bp;
    },

    boundFnObj(fn, fnObj, ...args) {
      const argsArr = [...args];
      let fnBound;

      if (argsArr.length > 0) {
        fnBound = fn.bind(null, fnObj, ...args);
      } else {
        fnBound = fn.bind(null, fnObj);
      }
      return fnBound;
    },
    matchBp(media, fnBound) {
      if (media.matches) {
        console.log("Added Rules");
        fnBound(false);
      } else {
        console.log("Removed Rules");
        fnBound(true);
      }
    },

    invokeBpFn(bpObj, fnBound) {
      if (bpObj) {
        const bp = this.breakpoint(bpObj.width, bpObj.minmax, bpObj.unit);

        this.matchBp(bp, fnBound);
        const fnFinal = () => this.matchBp(bp, fnBound);
        return { bp, fnFinal };
      }
    },
    invokeBpListener(eventBpObj) {
      if (eventBpObj) {
        const bp = eventBpObj.bp;
        const fnFinal = eventBpObj.fnFinal;
        bp.addListener(fnFinal);
      }
    },

    setMediaLogic(bpObj, fnType, fnObj, ...args) {
      if (bpObj) {
        const fnBound = this.boundFnObj(fnType, fnObj, ...args);
        const invokeBoundFn = this.invokeBpFn(bpObj, fnBound);
        this.invokeBpListener(invokeBoundFn);
      }
    }
  }
};
</script>

<!-- 
  
  //  Parent.vue File Properties
  //  Example Data to be passed on to Component 

  
  data() {

    const mediaObj = {
      width: 900,
      minmax: "min",
      unit: "px"
    };

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

    const evObj = {
      evt: "container",
      elt: "slide",
      events: {
        onmouseover: {
          background: "crimson",
          opacity: 1
        },
        onmouseleave: {
          background: "blue",
          opacity: 0
        }
      }
    };

    const all = {
      mediaObj,
      styleObj,
      evObj,
    };


    return {
      all,
      mediaObj: all.mediaObj,
      styleObj: all.styleObj,
      evObj: all.evObj,
    };
  },

-->

<!-- 
  
  //  Parent.vue File
  //  Example Component Prop Attribute
  

  // Pass as Data Property
    <template>
    <btn-component
      :btn-bp="mediaObj"
      :btn-style="styleObj"
      :btn-event="eventObj"
    >
    </btn-component>
    </template>


  // Pass as a Method
    <template>
    <btn-component
      :btn-bp="mediaObj()"
      :btn-style="styleObj()"
      :btn-event="eventObj()"
    >
    </btn-component>
    </template>

-->

<!-- 
  
  //  @Component.vue File
  //  Example Component Prop Recieved
  
  
  //  Import MediaMatch.vue
  import mediaMatch from "@/mixins/mediaMatch.vue";

  
  //  Component.vue File Properties
  props: {
    btnBp: Object,
    btnStyle: Object,
    btnEvent: Object,
  },
  data() {
    return {
      bpObj: this.btnBp,
      styleObj: this.btnStyle,
      eventObj: this.btnEvent,
    };
  },
  mixins: [mediaMatch],


  //  Example Executing Mixin Functions 
  mounted() {


    //  Mixin Function Arguements
    this.setMediaLogic(
      Media Query Object,
      Another Mixin Function Type,
      Function's Data Object,
      ...Additional Arguements
    );


    //  mediaMatch Mixin Functions for Styles
    this.setMediaLogic(
      this.bpObj,
      this.invokeStyles,
      this.styleObj
    );


    //  mediaMatch Mixin Functions for Events
    this.setMediaLogic(
      this.bpObj,
      this.invokeListener,
      this.eventObj
    );
  }

-->
