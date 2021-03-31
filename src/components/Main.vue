<template>
  <div class="main">
    <Toolbar :colors="colors" :defaultStyle="defaultStyle" />

    <div class="container">
      <Sheet
        class="main__sheet"
        :colors="colors"
        :defaultStyle="defaultStyle"
      />
    </div>
  </div>
</template>

<script>
import Sheet from "./Sheet";
import Toolbar from "./Toolbar";

export default {
  data: () => ({
    colors: {
      black: "#000",
      white: "#fff",
      red: "#FF0000",
      yellow: "#FFFF00",
    },
    defaultStyle: {
      color: "black",
      "font-size": "medium",
      background: "",
    },
  }),
  components: {
    Sheet,
    Toolbar,
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/styles/styles.scss";

.main {
  &__sheet {
    margin: 40px auto 10px;
  }
}
</style>