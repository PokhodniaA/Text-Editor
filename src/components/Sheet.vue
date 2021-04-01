<template>
  <div class="sheet" contenteditable="true" :style="style">
    <p>Some text</p>
  </div>
</template>

<script>
export default {
  computed: {
    // Set up default style
    style() {
      const defaultStyle = this.defaultStyle;

      return Object.keys(defaultStyle).reduce(
        (style, key) =>
          key === "color" || key === "background"
            ? style + `${key}: ${this.colors[defaultStyle[key]] || ""}; `
            : style + `${key}: ${defaultStyle[key]}; `,
        ""
      );
    },
  },
  props: {
    colors: Object,
    defaultStyle: Object,
  },
};
</script>

<style lang="scss" scoped>
.sheet {
  width: 80vw;
  height: calc(1.41 * 80vw);
  padding: 40px;

  border: none;
  outline: none;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);

  @media screen and (max-width: 700px) {
    width: 95vw;
  }
}
</style>