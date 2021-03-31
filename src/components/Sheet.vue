<template>
  <div class="sheet" contenteditable="true">
    <p>Some text</p>
  </div>
</template>

<script>
export default {};
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