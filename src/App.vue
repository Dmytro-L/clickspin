<template>
  <HelloView />
</template>

<script>
import HelloView from "./components/HelloView.vue";

export default {
  name: "App",
  components: {
    HelloView,
  },
};
</script>

<style lang="scss">
@import "./assets/scss/fonts.scss";
@import "./assets/scss/responsive.scss";
* {
  box-sizing: border-box;
}
body {
  padding: 0;
  margin: 0;
}
html {
  font-size: calc(100vw / 160);
  font-family: "Gotham Pro";
}
</style>
