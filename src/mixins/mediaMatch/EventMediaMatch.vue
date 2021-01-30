<script>
export default {
  methods: {
    eventStyles(el, styleObj, unset) {
      if (styleObj) {
        if (unset === false) {
          for (const style in styleObj) {
            el.style[style] = styleObj[style];
          }
        } else {
          for (const style in styleObj) {
            el.style[style] = "";
          }
        }
      }
    },
    eventObjects(evt, elemsObj, unset) {
      if (elemsObj) {
        for (const el in elemsObj) {
          let ref;

          if (el === "link") {
            if (this.$refs[el]) {
              ref = this.$refs[el];
            } else {
              ref = evt.children[3];
            }
          } else {
            ref = this.$refs[el];
          }
          this.eventStyles(ref, elemsObj[el], unset);
        }
      }
    },
    eventListener(evt, events, unset) {
      if (events) {
        if (unset === false) {
          for (const event in events) {
            evt[event] = this.eventObjects.bind(
              null,
              evt,
              events[event],
              false
            );
          }
        } else {
          for (const event in events) {
            evt[event] = this.eventObjects.bind(null, evt, events[event], true);
          }
        }
      }
    },
    invokeListener(obj, unset) {
      if (obj) {
        const evt = this.$refs[obj.evt];
        this.eventListener(evt, obj.events, unset);
      }
    }
  }
};
</script>

<!-- 

  //  Parent.vue File Properties
  //  Example Data to be passed on to Component 


  data() {

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
      evObj,
    };


    return {
      all,
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
      :btn-event="eventObj"
    >
    </btn-component>
    </template>


  // Pass as a Method
    <template>
    <btn-component
      :btn-event="eventObj()"
    >
    </btn-component>
    </template>

-->

<!-- 
  
  //  @Component.vue File
  //  Example Component Prop Recieved
  
  
  //  Import EventMediaMatch.vue
  import EventMediaMatch from "@/mixins/EventMediaMatch.vue";

  
  //  Component.vue File Properties
  props: {
    btnEvent: Object,
  },
  data() {
    return {
      eventObj: this.btnEvent,
    };
  },
  mixins: [EventMediaMatch],

-->
