<template>
  <div class="checkbox-custom">
    <input type="checkbox" id="myCheckbox" />
    <label for="myCheckbox"></label>
  </div>
</template>

<script>
export default {
  name: "CheckboxCustom",
};
</script>

<style lang='scss' scoped>
input[type="checkbox"] {
  display: none;
}

label {
  display: inline-block;
  width: 1.5rem;
  height: 1.5rem;
  background-color: transparent;
  border: 1px solid #999999;
}
input[type="checkbox"]:checked + label {
  background-image: url("@/assets/img/checked.png");
  background-size: cover;
  border: 1px solid transparent;
}
</style>