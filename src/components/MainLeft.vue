<template>
  <div class="left">
    <div class="left__wrapper">
      <div class="left__logo">
        <img src="../assets/img/logo.png" alt="logo-clickspin" />
        <img src="../assets/img/ClickSPIN.png" alt="logo-clickspin-text" />
      </div>
      <div class="left__description">
        <div>
          <span class="left__description-thin">
            deposit 500, get 500 usdt
          </span>
          <span class="left__description-gold"> as a gift </span>
        </div>
        <p class="left__description-blur">100% cashback for VIPs only</p>
      </div>
      <div class="left__button">
        <button @click="openPopup">BECOME A VIP-PLAYER</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MainLeft",
  setup(props, { emit }) {
    const openPopup = () => {
      emit("open-popup");
    };
    return {
      openPopup,
    };
  },
};
</script>

<style lang="scss" scoped>
.left {
  width: 50vw;
  height: 100vh;
  background-color: black;
  display: flex;
  &__wrapper {
    margin: 20% auto 0;
    width: 60%;
  }

  &__description-thin {
    font-size: 5rem;
    line-height: 6rem;
    font-weight: 600;
    color: white;
    text-transform: uppercase;
    margin: 0;
  }

  &__description-gold {
    font-size: 5rem;
    line-height: 6rem;
    font-weight: 500;
    color: #ebbe7d;
    text-transform: uppercase;
    margin: 0;
  }
  &__description-blur {
    font-size: 2rem;
    line-height: 2.75rem;
    font-weight: 600;
    color: #999999;
    text-transform: uppercase;
    margin: 0;
    margin-bottom: 6.5rem;
    margin-top: 4rem;
  }

  &__logo {
    display: flex;
    align-items: center;
    img:nth-child(1) {
      width: 4.66rem;
    }
    img:nth-child(2) {
      margin-left: 1.3rem;
      width: 13.66rem;
    }
    margin-bottom: 2.5rem;
  }
  &__button {
    button {
      font-size: 1.66rem;
      font-weight: 600;
      line-height: 2rem;
      color: #0b0b0a;
      padding: 1.3rem 4.5rem;
      border-radius: 56px;
      background-color: #ebbe7d;
      border: none;
      transition: 0.4s;
      cursor: pointer;

      &:hover {
        background-color: #fcfcfc;
        transition: 0.4s;
      }
    }
  }
}
</style>