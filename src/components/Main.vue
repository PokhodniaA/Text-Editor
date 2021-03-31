<template>
  <div class="main">
    <Toolbar :colors="colors" />

    <div class="container">
      <Sheet class="main__sheet" />
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