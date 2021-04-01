<template>
  <div class="main">
    <Toolbar :colors="colors" :defaultStyle="defaultStyle" @toJSON="showJSON" />

    <div class="main__main">
      <Sheet
        class="main__sheet"
        :colors="colors"
        :defaultStyle="defaultStyle"
        ref="text"
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
  methods: {
    showJSON() {
      // Show in console JSON
      console.log(this.parseJSON(this.$refs.text.$el));
    },
    parseJSON(element) {
      // Result array
      const model = [];

      // Find style in parrent elements
      const findStyle = (element, value) => {
        if (element.parentNode.style[value]) {
          return element.parentNode.style[value];
        } else if (element.tagName == "DIV") {
          return "";
        } else {
          return findStyle(element.parentNode, value);
        }
      };

      // Add text node into model
      const TextElem = (element) => {
        model.push({
          text: element.textContent,
          color: findStyle(element, "color"),
          fontSize: findStyle(element, "fontSize"),
          "background-color": findStyle(element, "background-color"),
        });
      };

      // Looking for text node
      const fromNode = (element) => {
        switch (element.nodeType) {
          case 3:
            return TextElem(element);
          default:
            return Elem(element);
        }
      };

      const Elem = (element) => {
        element.childNodes.forEach((child) => {
          fromNode(child);
        });
      };

      Elem(element);
      return JSON.stringify(model, null, "  ");
    },
  },
  components: {
    Sheet,
    Toolbar,
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/styles/styles.scss";

.main {
  &__main {
    display: flex;
    align-items: center;
    flex-direction: column;
  }

  &__sheet {
    margin: 40px auto 10px;
  }
}
</style>