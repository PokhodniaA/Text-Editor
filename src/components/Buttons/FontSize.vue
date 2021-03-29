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
    fontSize: 14,
  }),
  methods: {
    increaseFont() {
      this.fontSize++;
    },
    decreaseFont() {
      this.fontSize--;
    },
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

  button {
    border: none;
    background: none;
    outline: none;
    font-size: 1.5rem;

    transition: 0.3s;
    &:hover {
      cursor: pointer;
      background: #f48fb1;
    }
  }
}
</style>