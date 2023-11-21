<template>
  <div class="right">
    <img src="../assets/img/title-img.png" alt="title" class="right__title" />
    <img src="../assets/img/girl.png" alt="girl" class="right__girl" />
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss">
.right {
  background-image: url("@/assets/img/image_right.png");
  width: 50vw;
  height: 100vh;
  background-position: left center;
  position: relative;

  &__title {
    position: absolute;
    top: 15%;
    left: 50%;
    transform: translateX(-50%);
    width: 10vw;
  }
  &__girl {
    position: absolute;
    bottom: 0;
    left: 10%;
    width: 31.8vw;
  }
}
</style>