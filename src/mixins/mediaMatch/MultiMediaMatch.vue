<script>
import MediaMatch from "./MediaMatch.vue";
import StyleMediaMatch from "./StyleMediaMatch.vue";
import EventMediaMatch from "./EventMediaMatch.vue";

export default {
  mixins: [MediaMatch, StyleMediaMatch, EventMediaMatch],
  methods: {
    setMultiMediaLogic(bpObj, typeObj, ...args) {
      if (bpObj) {
        if (typeObj) {
          if (typeObj.styles) {
            for (const objStyle in typeObj.styles) {
              this.setMediaLogic(
                bpObj,
                this.invokeStyles,
                typeObj.styles[objStyle],
                ...args
              );
            }
          }

          if (typeObj.events) {
            for (const objEvent in typeObj.events) {
              this.setMediaLogic(
                bpObj,
                this.invokeListener,
                typeObj.events[objEvent],
                ...args
              );
            }
          }
        }
      }
    }
  }
};
</script>

<!-- 

  //  Parent.vue File  
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

    const container = {
      evt: "container",
      events: {
        onmouseover: {
          slide: {
            background: styles.cPrimary
          },
        },
        onmouseleave: {
          link: {
            color: styles.cSecondary
          },
        }
      }
    };


    const fnTypes = {
      styles: {
        mqStyles: styleObj
      },
      events: {
        containerEvent: container,
      }
    };

    const all = {
      mediaObj,
      styleObj,
      evObj,
      fnTypes
    };


    return {
      all,
      fnTypes: all.fnTypes
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
      :btn-multi-obj="fnTypes"
    >
    </btn-component>
    </template>


  // Pass as a Method
    <template>
    <btn-component
      :btn-bp="mediaObj()"
      :btn-multi-obj="fnTypes()"
    >
    </btn-component>
    </template>

-->

<!-- 
  
  //  @Component.vue File
  //  Example Component Prop Recieved
  
  
  //  Import MultiMediaMatch.vue
  import MultiMediaMatch from "@/mixins/MultiMediaMatch.vue";

  
  //  Component.vue File Properties
  props: {
    btnBp: Object,
    btnMultiObj: Object
  },
  data() {
    return {
      bpObj: this.btnBp,
      multiObj: this.btnMultiObj
    };
  },
  mixins: [MultiMediaMatch],


  //  Example Executing Mixin Functions 
  mounted() {


    //  Mixin Function Arguements
    this.setMultiMediaLogic(
      Media Query Object, 
      Data Object,
      ...Additional Arguements
    );
    

    //
    this.setMultiMediaLogic(
      this.bpObj, 
      this.multiObj
    );

  }

-->
