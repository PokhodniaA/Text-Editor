<template>
  <div class="toolbar">
    <div class="container">
      <div class="toolbar__row">
        <span class="toolbar__title">Text Editor</span>
        <div class="toolbar__buttons">
          <ColorPicker :defaultColor="'Black'">Color</ColorPicker>
          <ColorPicker>Background</ColorPicker>
          <FontSize />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ColorPicker from "./Buttons/ColorPicker";
import FontSize from "./Buttons/FontSize";

export default {
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

    width: 20%;
  }
}
</style>