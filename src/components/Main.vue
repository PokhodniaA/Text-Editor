<template>
  <div class="main">
    <Toolbar />

    <div class="container">
      <Sheet class="main__sheet" />
    </div>
  </div>
</template>

<script>
import Sheet from "./Sheet";
import Toolbar from "./Toolbar";

export default {
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
    margin: 50px auto 0;
  }
}
</style>