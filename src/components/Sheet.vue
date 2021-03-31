<template>
  <div class="sheet" contenteditable="true">
    <p :style="style">Some text</p>
  </div>
</template>

<script>
export default {
  methods: {
    foo() {
      console.log("change");
    },
  },
  computed: {
    style() {
      const defaultStyle = this.defaultStyle;

      return Object.keys(defaultStyle).reduce(
        (style, key) =>
          key === "color" || key === "background"
            ? style + `${key}: ${this.colors[defaultStyle[key]]}; `
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
  width: 80%;
  height: 80vh;
  padding: 40px;

  border: none;
  outline: none;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);

  p {
    font-size: medium;
    color: black;
  }
}
</style>