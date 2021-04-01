<template>
  <div class="picker">
    <button
      class="picker__button"
      :class="{ active: show }"
      @click="show = !show"
    >
      <slot></slot>
    </button>

    <transition name="fade" appear>
      <ul class="picker__dropdown-content" v-if="show">
        <li
          v-for="(hash, color) in colors"
          :key="color"
          @click="setNewColor(hash)"
        >
          {{ color }}
        </li>
      </ul>
    </transition>
  </div>
</template>

<script>
export default {
  data: () => ({
    show: false,
  }),
  methods: {
    setNewColor(color) {
      document.execCommand("styleWithCSS", true, null);

      switch (this.type) {
        case "color":
          document.execCommand("foreColor", false, color);
          break;
        case "background":
          document.execCommand("hiliteColor", false, color);
          break;
        default:
          break;
      }
    },
  },
  props: {
    type: String,
    colors: Object,
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/styles/styles.scss";

.picker {
  position: relative;

  &__button {
    @include toolButton;

    height: 100%;
  }

  &__dropdown-content {
    position: absolute;
    top: 100%;
    left: 50%;
    padding: 12px 0;
    width: max-content;

    background-color: #f9f9f9;
    box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
    z-index: 1;

    transform: translateX(-50%);

    li {
      padding: 5px 20px;

      list-style: none;
      user-select: none;

      transition: 0.3s;

      &:hover {
        background: #f48fb1;
        cursor: pointer;
      }
    }
  }
}

// Modifications

.active {
  border-bottom: 1px solid #f48fb1;
}

// Animations

.fade-enter-active,
.fade-leave-active {
  transition: all 0.3s ease-out;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>