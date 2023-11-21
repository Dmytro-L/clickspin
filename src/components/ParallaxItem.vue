<template>
  <div class="1">
    <slot :position-style="positionStyle" :data="data"></slot>
  </div>
</template>


<script>
import { computed } from "vue";

export default {
  name: "ParallaxItem",
  props: {
    data: {
      type: Object,
      required: true,
    },
    mousePositionY: {
      type: Number,
    },
    mousePositionX: {
      type: Number,
    },
  },
  setup(props) {
    const positionStyle = computed(() => {
      if (props.data.rotate) {
        return {
          transform: `translate(${
            props.mousePositionX / props.data.transformIndex
          }px, ${props.mousePositionY / props.data.transformIndex}px) rotate(${
            props.mousePositionX / props.data.transformIndex
          }deg)`,
        };
      }
      return {
        transform: `translate(${
          props.mousePositionX / props.data.transformIndex
        }px, ${props.mousePositionY / props.data.transformIndex}px)`,
      };
    });

    return {
      positionStyle,
    };
  },
};
</script>