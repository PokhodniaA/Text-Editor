<template>
  <div class="size">
    <button @click="decreaseFont">-</button>
    <span>{{ fontSize }}</span>
    <button @click="increaseFont">+</button>
  </div>
</template>

<script>
export default {
  data: () => ({
    fontSize: 0,
  }),
  methods: {
    increaseFont() {
      if (this.fontSize < 7) {
        this.changeFontSize(++this.fontSize);
      }
    },
    decreaseFont() {
      if (this.fontSize > 1) {
        this.changeFontSize(--this.fontSize);
      }
    },
    changeFontSize(size) {
      document.execCommand("styleWithCSS", true, null);
      document.execCommand("fontSize", false, size);
    },
  },
  props: {
    defaultStyle: Object,
  },
  mounted() {
    // Set up default font size
    switch (this.defaultStyle["font-size"]) {
      case "x-small":
        this.fontSize = 1;
        break;
      case "small":
        this.fontSize = 2;
        break;
      case "medium":
        this.fontSize = 3;
        break;
      case "large":
        this.fontSize = 4;
        break;
      case "x-large":
        this.fontSize = 5;
        break;
      case "xx-large":
        this.fontSize = 6;
        break;
      case "xxx-large":
        this.fontSize = 7;
        break;

      default:
        this.fontSize = 3;
        break;
    }
  },
};
</script>

<style lang="scss" scoped>
.size {
  display: flex;
  justify-content: space-between;
  align-items: center;

  font-size: 1rem;

  border: 1px solid #2c3e50;
  border-radius: 2px;

  span {
    padding: 0 4px;
  }

  button {
    border: none;
    background: none;
    outline: none;
    user-select: none;

    font-size: 1.5rem;

    transition: 0.3s;
    &:hover {
      cursor: pointer;
      background: #f48fb1;
    }
  }
}
</style>