<template>
  <div v-if="cocktail" class="wrap">
    <AppLayout :imgUrl="cocktail.strDrinkThumb">
      <div class="info">
        <div class="info__inner">
          <h1 class="info__title">{{ cocktail.strDrink }}</h1>

          <div class="info__text">
            Try our delicious cocktail recipes for every occasion. Find
            delicious cocktail recipes by ingredient through our cocktail
            generator.
          </div>
        </div>
      </div>
    </AppLayout>
  </div>
</template>
<script setup>
import axios from "axios";
import { ref, computed } from "vue";
import { useRoute } from "vue-router";
import AppLayout from "../components/AppLayout.vue";
import { COCKTAIL_BY_ID } from "@/constants";

const route = useRoute();

const cocktail = ref(null);
const cocktailId = computed(() => route.path.split("/").pop());

async function getCocktail() {
  const data = await axios.get(`${COCKTAIL_BY_ID}${cocktailId.value}`);
  cocktail.value = data?.data?.drinks[0];
}

getCocktail();
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
  &__text {
    color: $text-muted;
    margin: 0 auto;
    text-align: center;
    font-size: 16px;
    line-height: 36px;
    letter-spacing: 0.1em;
    max-width: 516px;
  }
}
</style>
