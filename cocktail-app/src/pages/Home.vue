<template>
  <AppLayout imgUrl="'/src/assets/img/bg-1.jpg'">
    <div class="info">
      <div class="info__inner">
        <h1 class="info__title">Choose your drink</h1>
        <div class="info__select">
          <el-select
            v-model="ingredient"
            placeholder="Choose main ingredient"
            class="select"
          >
            <el-option
              v-for="item in ingredients"
              :key="item.strIngredient1"
              :label="item.strIngredient1"
              :value="item.strIngredient1"
            />
          </el-select>
        </div>
        <div class="info__text">
          Try our delicious cocktail recipes for every occasion. Find delicious cocktail recipes by ingredient through our cocktail generator.
        </div>
      </div>
    </div>
  </AppLayout>
</template>
<script setup>
import { ref } from 'vue';
import AppLayout from "../components/AppLayout.vue";
import { useRootStore } from "../stores/root";
import { storeToRefs } from "pinia";

const rootStore = useRootStore();
rootStore.getIngredients();

const { ingredients } = storeToRefs(rootStore);
const ingredient = ref(null)
</script>
<style lang="scss" scoped>
@import "@/assets/styles/main.scss";

.info {
  display: flex;
  align-items: center;
  justify-content: center;
  &__inner {
    padding: 80px 0;
    text-align: center;
  }
  &__select {
    margin: 50px auto;
    width: 220px;
  }
  &__text {
    color: $text-muted;
    margin: 0 auto;
    text-align: center;
    font-size: 16px;
    line-height: 36px;
    letter-spacing: .1em;
    max-width: 516px;
  }
}
</style>
