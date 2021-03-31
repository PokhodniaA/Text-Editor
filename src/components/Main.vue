<template>
  <div class="main">
    <Toolbar :colors="colors" :defaultStyle="defaultStyle" @toJSON="toJSON" />

    <div class="container">
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
    toJSON() {
      //   console.log(this.$refs.text.$el);
      console.log(this.parseJSON(this.$refs.text.$el));
    },
    parseJSON(element) {
      const findStyle = (e, value) => {
        if (e.parentNode.style[value] && e.tagName !== "DIV") {
          return e.parentNode.style[value];
        } else if (e.tagName == "DIV") {
          console.log("div,", value);
          return "";
        } else {
          return findStyle(e.parentNode, value);
        }
      };

      const TextElem = (e) => ({
        toJSON: () => ({
          text: e.textContent,
          //   color: e.parentNode.style.color,
          //   fontSize: e.parentNode.style.fontSize,
          //   "background-color": e.parentNode.style["background-color"],
          color: findStyle(e, "color"),
          fontSize: findStyle(e, "fontSize"),
          "background-color": findStyle(e, "background-color"),
        }),
      });

      const Elem = (e) => ({
        toJSON: () => ({
          tagName: e.tagName,
          children: Array.from(e.childNodes, fromNode),
        }),
      });

      // fromNode :: Node -> Elem
      const fromNode = (e) => {
        switch (e.nodeType) {
          case 3:
            return TextElem(e);
          default:
            return Elem(e);
        }
      };

      // html2json :: Node -> JSONString
      const html2json = (element) => JSON.stringify(Elem(element), null, "  ");

      console.log(html2json(element), "test");
      console.dir(element, "element");
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
  &__sheet {
    margin: 40px auto 10px;
  }
}
</style>