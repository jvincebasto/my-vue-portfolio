<script>
export default {
  methods: {
    matchRefStr(str, num = 1, strMatch = " ") {
      return str.substring(0, num) === strMatch ? true : false;
    },
    appCompRefs(refsObj, refs) {
      for (const ref in refs) {
        if (ref == "bubbleSlider") {
          refsObj[ref] = refs[ref];
        }
        if (this.matchRefStr(ref, 5, "nlink")) {
          refsObj.navLinks[ref] = refs[ref];
        }
        if (this.matchRefStr(ref, 4, "sect")) {
          if (ref !== "sectNav") {
            refsObj.sections[ref] = refs[ref];
          }
        }
      }
    },
    homeCompRefs(refsObj, refs) {
      for (const ref in refs) {
        if (this.matchRefStr(ref, 4, "sect")) {
          refsObj.sections[ref] = refs[ref];
        }
      }
    },
    collectRefs(refsObj, parentRefs, callback) {
      for (const ref in parentRefs) {
        const obj = parentRefs[ref].$refs;
        callback(refsObj, obj);
      }
    }
  }
};
</script>
