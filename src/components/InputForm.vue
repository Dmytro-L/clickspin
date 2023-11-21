<template>
  <div class="form-input">
    <input
      autocomplete="off"
      ref="inputRef"
      @input="validateInput"
      v-model="inputValue"
      :minlength="params.minLength"
      :type="params.type"
      :id="params.type"
    />
    <label
      :class="{ active: inputValue.length }"
      class="label"
      :for="params.type"
      >{{ params.placeholder }}</label
    >
    <span class="form-icon"
      ><img :src="require(`@/assets/img/${params.icon}`)" alt="icon"
    /></span>
    <p class="error">{{ params.errorMessage }}</p>
  </div>
</template>

<script>
import { ref, watch } from "vue";

export default {
  name: "InputForm",
  props: {
    params: {
      type: Object,
      required: true,
    },
  },
  setup(props, { emit }) {
    const inputValue = ref("");
    const inputRef = ref(null);

    watch(inputValue, (value) => {
      emit("update:modelValue", value);
    });

    const validateInput = () => {
      const isValid = inputRef.value.checkValidity();
      emit("valid", isValid);
    };

    const showError = ref(false);

    return {
      inputRef,
      inputValue,
      showError,
      validateInput,
    };
  },
};
</script>
<style lang="scss" scoped>
.form-input {
  position: relative;
  .label {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    color: #999999;
    font-size: 1.16rem;
    font-weight: 400;
    line-height: 1.33;
    left: 2.82rem;
    transition: all 0.4s;
  }
  .form-icon {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    left: 1.33rem;
    img {
      width: 1.33rem;
    }
  }
  input {
    all: unset;
    width: calc(100% - 3.99rem);
    border: 1px solid;
    border-color: #353535;
    border-radius: 8px;
    background-color: transparent;
    transition: border-color 0.4s;
    padding: 1.33rem;
    padding-left: 2.66rem;
    font-size: 1.15rem;
    line-height: 1.33rem;
    left: 2.82rem;
    color: #999999;

    &:focus-visible {
      outline: none;
    }

    &:hover,
    &:focus {
      border-color: #fcfcfc;
      transition: border-color 0.4s;
    }
  }
  input:hover ~ .label {
    color: #999999;
  }
  input:focus ~ .label {
    font-size: 0.9rem;
    top: 0;
    background: black;
    padding: 0 0.33rem;
    transition: all 0.4s;
    color: #999999;
  }
  .error {
    position: absolute;
    right: 1.7rem;
    bottom: 0;
    transform: translateY(50%);
    color: transparent;
    margin: 0;
    z-index: -1;
    transition: all 0.4s;
  }
  input:invalid {
    border-color: red;
    transition: all 0.4s;
  }

  input:invalid ~ .error {
    color: red;
    z-index: 11;
    background: black;
    transition: all 0.4s;
    padding: 0 0.33rem;
  }

  .label.active {
    font-size: 0.9rem;
    top: 0;
    background: black;
    padding: 0 0.33rem;
    transition: all 0.4s;
    color: #999999;
  }
}
</style>