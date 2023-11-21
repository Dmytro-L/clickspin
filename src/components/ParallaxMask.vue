<template>
  <ParallaxItem
    v-for="item in parallaxItemsList"
    :data="item"
    :mouse-position-y="setParallaxStyleY"
    :mouse-position-x="setParallaxStyleX"
    :key="item.id"
    v-slot="slotProps"
  >
    <img
      :style="!stylePopupActive ? slotProps.positionStyle : ''"
      :src="require(`@/assets/img/${slotProps.data.img}`)"
      :class="slotProps.data.class"
      :alt="slotProps.data.alt"
    />
  </ParallaxItem>
</template>

<script>
import ParallaxItem from "./ParallaxItem.vue";
import { ref, onMounted, computed } from "vue";
import { parallaxItems } from "../assets/js/mocks";

export default {
  name: "ParallaxMasc",
  components: {
    ParallaxItem,
  },
  props: {
    disabledByPopup: {
      type: Boolean,
      default: false,
    },
  },
  setup(props) {
    const disableParallax = ref(false);
    const windowWidth = ref();
    const windowHeight = ref();
    const mouseX = ref();
    const mouseY = ref();
    const parallaxItemsList = ref(parallaxItems);

    onMounted(() => {
      handleSizeWindow();
      window.addEventListener("mousemove", (e) => {
        mouseX.value = e.pageX;
        mouseY.value = e.pageY;
      });
      window.addEventListener("resize", () => {
        handleSizeWindow();
      });
    });
    const stylePopupActive = computed(() => {
      return disableParallax.value || props.disabledByPopup;
    });

    const handleSizeWindow = () => {
      windowWidth.value = window.innerWidth;
      windowHeight.value = window.innerHeight;
      disableParallax.value = windowWidth.value < 1240;
    };

    const setParallaxStyleX = computed(() => {
      return mouseX.value - window.innerWidth / 2;
    });

    const setParallaxStyleY = computed(() => {
      return mouseY.value - window.innerHeight / 2;
    });

    return {
      setParallaxStyleY,
      setParallaxStyleX,
      parallaxItemsList,
      disableParallax,
      stylePopupActive,
    };
  },
};
</script>

<style lang="scss">
.brilliant_1,
.brilliant_2,
.chip,
.light_1,
.light_2,
.ballon,
.candy {
  position: absolute;
  top: 0;
  transition: 0.2s all;
}
.brilliant_1 {
  bottom: 8%;
  top: unset;
  left: 31%;
  width: 8vw;
}
.brilliant_2 {
  top: 34%;
  left: -6%;
  width: 15vw;
}
.chip {
  left: 44.7%;
  width: 19vw;
  top: -9%;
}
.light_2 {
  top: 12%;
  left: 39%;
  width: 10vw;
}
.light_1 {
  bottom: 15%;
  top: unset;
  left: 35%;
  width: 10vw;
}
.ballon {
  width: 35vw;
  right: -12%;
  top: -5%;
}
.candy {
  top: 46%;
  left: 42%;
  width: 13vw;
}
</style>