<template>
  <div class="main">
    <MainLeft @open-popup="openPopup" />
    <MainRight />
    <LoginPopup :is-open="isPopupOpened" @close-popup="closePopup" />
    <ParallaxMask :disabled-by-popup="isPopupOpened" />
  </div>
</template>

<script>
import MainLeft from "./MainLeft.vue";
import ParallaxMask from "./ParallaxMask.vue";
import MainRight from "./MainRight.vue";
import LoginPopup from "./LoginPopup.vue";
import { ref } from "vue";

export default {
  name: "HelloView",
  components: {
    MainLeft,
    MainRight,
    LoginPopup,
    ParallaxMask,
  },
  setup() {
    const isPopupOpened = ref(false);
    const closePopup = () => {
      isPopupOpened.value = false;
    };
    const openPopup = () => {
      isPopupOpened.value = true;
    };
    return {
      openPopup,
      closePopup,
      isPopupOpened,
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.main {
  display: flex;
  position: relative;
  overflow: hidden;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
