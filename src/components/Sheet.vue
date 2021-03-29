<template>
  <textarea autofocus name="main" wrap="soft" class="sheet">
Hello
  </textarea>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.sheet {
  width: 80%;
  height: 80vh;
  padding: 40px;

  resize: none;
  border: none;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);

  &:focus {
    outline: none;
  }
}
</style>