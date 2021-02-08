<script>
export default {
  methods: {
    observerOpt(threshold = 0.6) {
      const options = {
        threshold
      };

      return options;
    },
    observerFn(options, callbackFn) {
      const observer = new IntersectionObserver(callbackFn, options);

      return observer;
    },
    bubbleSliderFn(entry, refsObj, unset) {
      const bubbleSlider = refsObj.bubbleSlider;
      const nlinks = refsObj.navLinks;

      const section = entry.target.attributes["data-section"].value;

      let link;
      for (const nlink in nlinks) {
        if (nlink.toLowerCase().substring(5) === section) {
          link = nlinks[nlink].getBoundingClientRect();
        }
      }

      const props = {
        height: link.height,
        width: link.width,
        top: link.top,
        left: link.left
      };

      if (entry.isIntersecting) {
        if (unset === false) {
          // bubbleSlider.style.backgroud = entry.target.style.background;
          for (const prop in props) {
            bubbleSlider.style.setProperty(prop, `${props[prop]}px`);
          }
        } else {
          // bubbleSlider.style.display = "none";
          // bubbleSlider.style.backgroud = entry.target.style.background;
          for (const prop in props) {
            bubbleSlider.style.setProperty(prop, `${props[prop]}px`);
          }
        }
      }
    },
    invokeObserver(options, callbackFn, refsObj, unset) {
      const observer = this.observerFn(options, function(entries) {
        entries.forEach(entry => {
          callbackFn(entry, refsObj, unset);
        });
      });

      for (const sectObj in refsObj.sections) {
        const section = refsObj.sections[sectObj];
        observer.observe(section);
      }
    }
  }
};
</script>
