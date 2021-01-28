<template>
  <template v-if="type(typeObj)">
    <div class="btn btn-container" ref="container">
      <div class="btn-bg" ref="bg"></div>
      <div class="btn-slide" ref="slide"></div>
      <div class="btn-border" ref="border"></div>
      <a :href="link(typeObj)" ref="link">
        <slot name="title">Secondary Button - Link</slot>
      </a>
    </div>
  </template>
  <template v-else>
    <div class="btn btn-container">
      <div class="btn-bg"></div>
      <div class="btn-slide"></div>
      <div class="btn-border"></div>
      <label for="submit" class="btn-label">
        <slot name="title">Secondary Button Submit</slot>
      </label>
      <input id="submit" type="submit" />
    </div>
  </template>
</template>

<script>
export default {
  props: {
    btnType: Object,
    btnBp: Object,
    btnStyle: Object,
    btnEvent: Object,
    btnMultiObj: Object
  },
  data() {
    return {
      typeObj: this.btnType,
      bpObj: this.btnBp,
      styleObj: this.btnStyle,
      eventObj: this.btnEvent,
      multiObj: this.btnMultiObj
    };
  },
  methods: {
    type(obj) {
      if (obj) {
        if (obj.type === "link") {
          return true;
        } else {
          return false;
        }
      }
    },
    link(obj) {
      if (obj) {
        if (!obj.link) {
          return "#";
        } else {
          return obj.link;
        }
      }
    },

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
        for (const item in obj) {
          if (item) {
            const ref = this.$refs[item];
            this.addStyles(ref, obj[item], unset);
          }
        }
      }
    },

    eventTargets(ref) {
      if (ref) {
        const obj = {
          evt: this.$refs[ref.evt],
          elt: this.$refs[ref.elt]
        };
        return obj;
      }
    },
    eventStyles(evt, evStyles, unset) {
      if (evStyles) {
        if (unset === false) {
          for (const evStyle in evStyles) {
            evt.style[evStyle] = evStyles[evStyle];
          }
        } else {
          for (const evStyle in evStyles) {
            evt.style[evStyle] = "";
          }
        }
      }
    },
    eventListener(refs, events, unset) {
      if (events) {
        if (unset === false) {
          for (const event in events) {
            refs.evt[event] = this.eventStyles.bind(
              null,
              refs.elt,
              events[event],
              false
            );
          }
        } else {
          for (const event in events) {
            refs.evt[event] = this.eventStyles.bind(
              null,
              refs.elt,
              events[event],
              true
            );
          }
        }
      }
    },
    invokeListener(obj, unset) {
      if (obj) {
        // const refs = this.eventTargets(obj.evt,obj.elt);
        const refs = this.eventTargets(obj);
        this.eventListener(refs, obj.events, unset);
      }
    },

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
        let fnFinal;

        this.matchBp(bp, fnBound);
        fnFinal = () => this.matchBp(bp, fnBound);
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
    },
    setMultiMediaLogic(bpObj, typeObj, ...args) {
      // setMultiMediaLogic(bpObj,typeObj) {
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
  },
  mounted() {
    // this.setMediaLogic(this.bpObj,this.invokeStyles,this.styleObj);
    // this.setMediaLogic(this.bpObj,this.invokeListener,this.eventObj);

    this.setMultiMediaLogic(this.bpObj, this.multiObj);
  }
};
</script>

<style scoped lang="scss">
@use "./../sass/abstracts/abstracts" as abs;

.btn {
  display: inline-block;
  cursor: pointer;

  &-container {
    border-radius: 10rem;

    position: relative;
    overflow: hidden;

    @include abs.fns-respond(sptab) {
      height: 100%;
      width: 100%;
    }
  }

  & > * {
    display: block;
    height: 100%;
    width: 100%;

    position: absolute;
    top: 0;
    left: 0;

    border-radius: inherit;
    border: 0.2rem solid abs.$vars-c-darkblue;

    @include abs.fns-respond(sptab) {
      height: inherit;
      width: inherit;
      border-color: abs.$vars-c-lightblue;
    }
  }

  &-bg {
    background: transparent;
    border: none;
  }
  &-border {
    // border-color: abs.$vars-c-black;
  }

  &-slide {
    background: rgba(abs.$vars-c-lightblue, 0);
    border: none;
    width: 0;

    left: unset;
    right: 0;
    transform-origin: right;

    transition: all 0.3s ease-in-out;

    @include abs.fns-respond(lphone) {
      transition-duration: 0.5s;
    }
  }
  &:hover &-slide {
    background: rgba(abs.$vars-c-lightblue, 1);
    width: 100%;

    left: 0;
    transform-origin: left;

    @include abs.fns-respond(sptab) {
      background: rgba(abs.$vars-c-lightblue, 0.2);
    }
  }
  &:hover > a {
    color: abs.$vars-c-black;
    // font-weight: bold;

    @include abs.fns-respond(sptab) {
      color: rgba(abs.$vars-c-white, 0.8);
    }
  }

  & > a,
  &-label {
    cursor: inherit;
    font-family: tbody;
    font-size: 1.8rem;
    text-transform: uppercase;

    color: abs.$vars-c-darkblue;
    white-space: pre;

    border: none;
    padding: 1rem 3rem;

    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;

    @include abs.fns-respond(sptab) {
      font-family: tthin;
      color: abs.$vars-c-lightblue;
      font-weight: bold;
    }
  }
  & #submit {
    height: 0;
    width: 0;
    background: blue;
  }
}
</style>
