<template>
  <main class="recipes_list_wrapper">
    <recipe-item
      v-for="recipe in recipes"
      :key="recipe.id"
      :recipe="recipe"
    >
    </recipe-item>
  </main>
</template>

<script setup>

import RecipeItem from './RecipeItem.vue'
  const {recipes} = defineProps({
    recipes: Array
  })

</script>

<style>
  .recipes_list_wrapper {
    display: grid;
    grid-template-columns: repeat(3, auto);
    gap: 60px 75px;
    width: fit-content;
    margin: auto;
    margin-top: 60px;
    padding-bottom: 30px;
  }

</style>