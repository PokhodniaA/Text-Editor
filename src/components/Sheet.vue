<template>
  <div class="sheet" contenteditable="true">
    <p>Some text</p>
  </div>
</template>

<script>
export default {
  methods: {
    changeColor() {
      // document.execCommand("foreColor", false, "red");
      // Работает

      document.execCommand("styleWithCSS", true, null);
      document.execCommand("foreColor", false, "red");
    },
  },
  computed: {
    // Delete getFormat
    getFormat() {
      return {
        color: this.format.color,
        fontSize: `${this.format.size}px`,
        backgroundColor: this.format.background,
      };
    },
  },
  props: {},
  created() {
    // Потом удалить
    // Через anchornode и focusNode смогу брать узлы для json
    document.addEventListener("selectionchange", () => {
      // let {
      //   anchorNode,
      //   anchorOffset,
      //   focusNode,
      //   focusOffset,
      // } = document.getSelection();
      let selectedText = document.getSelection().toString();
      // this.changeColor();
      console.log(selectedText);
    });
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