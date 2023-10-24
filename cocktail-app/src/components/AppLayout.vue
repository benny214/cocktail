<template>
  <div class="root">
    <div :style="`background-image: url(${imgUrl})`" class="root__img"></div>
    <div class="root__main">
      <el-button class="main__btn">Get random cocktail</el-button>
      <slot></slot>
    </div>
  </div>
</template>
<script setup>
const props = defineProps({
  imgUrl : {
    type: String,
    required: true
  }
})
</script>
<style lang="scss" scoped>
  @import '../assets/styles/main.scss';

  .root {
    display: flex;
    background-color: $main-bg-c;
    min-height: 100vh;

    &__img {
      width: 50%;
      background-repeat: no-repeat;
      background-position: 50% 50%;
      background-size: cover;
    }

    &__main {
      width: 50%;
      position: relative;
      padding: 32px 40px;
    }
  }

  .main__btn {
    padding: 8px 16px;
    position: absolute;
    top: 32px;
    right: 40px;
    background-color: $accent;
    color: $text-c;
    font-size: 16px;
    font-weight: 400;
    border-width: 0;
    transition: all .2s linear;
    font-family: 'Raleway', 'Arial', sans-serif;

    &:hover,
    &:active{
      background-color: $accent-hov;
    }
  }
</style>