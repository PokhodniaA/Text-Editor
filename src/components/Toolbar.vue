<template>
  <div class="toolbar">
    <div class="container">
      <div class="toolbar__row">
        <span class="toolbar__title">Text Editor</span>
        <div class="toolbar__buttons">
          <ColorPicker :type="'color'" :colors="colors">Color</ColorPicker>
          <ColorPicker :type="'background'" :colors="colors"
            >Background</ColorPicker
          >
          <FontSize :defaultStyle="defaultStyle" />
          <button class="toolbar__json" @click="$emit('toJSON')">
            to JSON
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ColorPicker from "./Buttons/ColorPicker";
import FontSize from "./Buttons/FontSize";

export default {
  props: {
    colors: Object,
    defaultStyle: Object,
  },
  components: {
    ColorPicker,
    FontSize,
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/styles/styles.scss";

.toolbar {
  width: 100%;
  height: 80px;

  background: #e3f2fd;

  &__row {
    display: flex;
    justify-content: space-between;
    align-items: center;

    width: 100%;
    height: 80px;
    text-align: center;
  }
  &__title {
    font-size: 1.5rem;
    font-style: italic;
  }

  &__buttons {
    display: flex;
    justify-content: space-between;

    width: 30%;
  }

  &__json {
    height: 23px;
    background: none;
    border: none;
    border-bottom: 1px solid #2c3e50;
    font-size: 1rem;
    outline: none;
    transition: 0.3s;

    &:hover {
      cursor: pointer;
      color: #f48fb1;
      border-bottom: 1px solid #f48fb1;
    }
  }
}
</style>