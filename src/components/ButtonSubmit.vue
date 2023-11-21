<template>
  <button
    ref="buttonSubmit"
    @click="checkData"
    class="button-submit"
    :class="{ disable: !isDisable }"
  >
    {{ buttonText }}
  </button>
</template>

<script>
import { ref } from "vue";

export default {
  name: "ButtonSubmit",
  props: {
    isDisable: {
      type: Boolean,
    },
    emptyData: {
      type: Boolean,
    },
  },
  setup(props) {
    const buttonText = ref("Create an account");
    const buttonSubmit = ref(null);
    const checkData = () => {
      if (!props.emptyData) {
        buttonSubmit.value.textContent = "Set something )";
      }
      setTimeout(() => {
        buttonSubmit.value.textContent = buttonText.value;
      }, 5000);
    };
    return {
      checkData,
      buttonSubmit,
      buttonText,
    };
  },
};
</script>

<style lang="scss">
.button-submit {
  margin-top: 2.66rem;
  font-size: 1.13rem;
  font-weight: 500;
  background-color: #e4c086;
  border-radius: 10px;
  width: 100%;
  padding: 1.33rem;
  border: none;
  transition: 0.4s;
  cursor: pointer;

  &:hover {
    background-color: #fcfcfc;
    transition: 0.4s;
  }

  &.disable {
    background-color: #1c1c1c;
    color: #282828;
    transition: 0.4s;
  }
}
</style>