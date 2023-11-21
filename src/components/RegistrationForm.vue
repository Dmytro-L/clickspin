<template>
  <h2 class="title-form">Registration</h2>
  <InputForm
    @valid="setInputValid"
    :params="emailParamsInput"
    v-model="emailValue"
  />
  <InputForm
    @valid="setInputValid"
    :params="nameParamsInput"
    v-model="nameValue"
  />
  <div class="policy-block">
    <CheckboxCustom />
    <div class="policy-text">
      By checking this box when registering on this site, t he user confirms
      that he is over 18 years of age and has read, understood and accepted the
      <a class="link" href="#">Terms and Conditions.</a>
    </div>
  </div>
  <ButtonSubmit :empty-data="emptyData" :is-disable="isValid" />
  <div class="social-block">
    <h4>Or register with:</h4>
    <div class="social-icons">
      <a href="#">
        <img src="../assets/img/icon_socials.png" alt="social" />
      </a>
      <a href="#">
        <img src="../assets/img/icon_socials_1.png" alt="social" />
      </a>
      <a href="#">
        <img src="../assets/img/icon_socials_2.png" alt="social" />
      </a>
      <a href="#">
        <img src="../assets/img/icon_socials_3.png" alt="social" />
      </a>
    </div>
  </div>
</template>

<script>
import ButtonSubmit from "./ButtonSubmit";
import InputForm from "./InputForm";
import CheckboxCustom from "./CheckboxCustom";
import { ref, computed } from "vue";
import { emailParams, nameParams } from "../assets/js/mocks";

export default {
  name: "RegistrationForm",
  components: {
    InputForm,
    CheckboxCustom,
    ButtonSubmit,
  },
  setup() {
    const isValid = ref(true);
    const emailValue = ref("");
    const nameValue = ref("");
    const emailParamsInput = ref(emailParams);
    const nameParamsInput = ref(nameParams);

    const setInputValid = (inputIsValid) => {
      isValid.value = inputIsValid;
    };

    const emptyData = computed(() => {
      if (emailValue.value && nameValue.value) {
        return true;
      }
      return false;
    });

    return {
      nameValue,
      emailValue,
      emailParamsInput,
      nameParamsInput,
      isValid,
      setInputValid,
      emptyData,
    };
  },
};
</script>

<style lang="scss">
.policy-block {
  padding-top: 0.66rem;
  display: flex;
  width: 100%;
  .policy-text {
    padding-left: 0.66rem;
    font-size: 0.83rem;
    color: #999999;
    font-weight: 600;
    line-height: 1.13rem;
  }

  .link {
    text-decoration: none;
    color: #e4c086;
  }
}
.title-form {
  font-size: 1.66rem;
  color: #fcfcfc;
  text-align: center;
  margin-top: 7.33rem;
  margin-bottom: 4rem;
  font-weight: 400;
  letter-spacing: 0.1rem;
}
.form-input {
  margin-bottom: 2rem;
}

.social-block {
  margin-top: 2.66rem;
  h4 {
    margin: 0;
    font-size: 1rem;
    color: #fcfcfc;
    text-align: center;
    margin-bottom: 1rem;
  }
  .social-icons {
    display: flex;
    gap: 0.66rem;
    justify-content: center;
    img {
      transition: 0.4s;
      width: 4rem;
    }
    img:hover {
      transform: scale(1.1);
      transition: 0.4s;
    }
  }
}
</style>