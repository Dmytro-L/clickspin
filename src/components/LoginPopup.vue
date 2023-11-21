<template>
  <div class="popup" :class="{ active: isOpen }">
    <div class="popup__wrapper">
      <div class="mobile">
        <img class="popup-candy_1" src="../assets/img/image_4.png" alt="img" />
        <img class="popup-candy_2" src="../assets/img/image_4.png" alt="img" />
        <img class="popup-ballon" src="../assets/img/image_3.png" alt="img" />
        <img class="popup-girl" src="../assets/img/girl.png" alt="img" />
        <div class="logo">
          <img
            src="../assets/img/logo.png"
            alt="logo-clickspin"
            class="logo-item"
          />
          <img
            src="../assets/img/ClickSPIN.png"
            alt="logo-clickspin-text"
            class="logo-item"
          />
        </div>
        <div class="description">
          <div>
            <span class="description-text">
              deposit 500,<br />
              get 500 usdt as a gift
            </span>
          </div>
          <p class="description-gold">100% cashback for VIPs only</p>
        </div>
      </div>
      <img
        @click="closePopup"
        class="popup__button-close"
        src="../assets/img/button_close.png"
        alt="button_close"
      />
      <div class="popup__form">
        <RegistrationForm />
      </div>
    </div>
  </div>
</template>

<script>
import RegistrationForm from "./RegistrationForm";
export default {
  name: "LoginPopup",
  components: {
    RegistrationForm,
  },
  props: {
    isOpen: {
      type: Boolean,
    },
  },
  setup(props, { emit }) {
    const closePopup = () => {
      emit("close-popup");
    };
    return {
      closePopup,
    };
  },
};
</script>

<style lang=scss>
.popup {
  font-family: "Stolzl";

  .mobile {
    display: none;
    position: relative;
    overflow: hidden;
    .popup-girl {
      position: absolute;
      bottom: 0;
      width: 150px;
      left: 50%;
      transform: translateX(-50%);
    }
    .popup-candy_1 {
      position: absolute;
      bottom: -45px;
      width: 95px;
      transform: rotate(-85deg);
    }
    .popup-candy_2 {
      position: absolute;
      bottom: 90px;
      width: 87px;
      left: -26px;
    }
    .popup-ballon {
      position: absolute;
      bottom: 12px;
      width: 150px;
      right: -53px;
    }
    .description {
      text-align: center;
      text-transform: uppercase;
      font-weight: 500;
      margin-top: 24px;

      .description-text {
        color: #fcfcfc;
        font-size: 1.33rem;
      }
      .description-gold {
        margin-top: 8px;
        color: #e4c086;
        font-size: 1.33rem;
      }
    }
    .logo {
      text-align: center;
      margin-top: 33px;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      .logo-item:nth-child(1) {
        width: 32px;
      }
      .logo-item:nth-child(2) {
        width: 94px;
      }
    }
  }

  width: 100vw;
  height: 100vh;
  background-color: #01010193;
  position: absolute;
  top: 0;
  display: none;
  z-index: 10;

  &.active {
    display: flex;
  }

  &__button-close {
    position: absolute;
    top: 1.33rem;
    right: 1.33rem;
    z-index: 11;
    width: 3.33rem;
    transition: 0.4s;
    cursor: pointer;

    &:hover {
      transform: scale(1.1);
      transition: 0.4s;
    }
  }

  &__wrapper {
    width: 59.9rem;
    height: 58.6rem;
    display: flex;
    background-image: url("@/assets/img/Image_form.png");
    background-position: left center;
    background-size: contain;
    margin: auto;
    position: relative;
    background-repeat: no-repeat;
  }

  &__img {
    width: fit-content;
    height: 100%;

    img {
      height: 100%;
    }
  }

  &__form {
    background: black;
    width: 50%;
    height: 100%;
    position: absolute;
    right: 0;
    padding: 1.33rem;
  }
}
</style>