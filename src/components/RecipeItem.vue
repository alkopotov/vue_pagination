<template>
  <div class="recipe_wrapper">
    <img :src="recipe.image" alt="">
    <div class="recipe_details">
      <h2>{{ recipe.name }}</h2>
      <p>Difficulty: {{ recipe.difficulty }}</p>
      <p>Cuisine: {{ recipe.cuisine  }}</p>
      <p>Calories per Serving: {{ recipe.caloriesPerServing }}</p>
      <h3>Ingredients:</h3>
      <ul>
        <li v-for="(ingredient, index) in recipe.ingredients" :key="index">{{ ingredient }}</li>
      </ul>
    </div>
  </div>
</template>

<script setup>
  const {recipe} = defineProps({
    recipe: {}
  })

</script>

<style>
  .recipe_wrapper {
    width: 224px;
    display: flex;
    flex-direction: column;
    box-shadow: 0px 4px 4px 0px #00000040;
    border-radius: 25px;
  }

  .recipe_wrapper img {
    width: 100%;
    border-radius: 25px 25px 0 0;
    height: 177px;
    object-fit: cover;
  }

  .recipe_wrapper h2 {
    font-size: 16px;
    font-weight: 700;
    line-height: 19px;
    letter-spacing: 0em;
    text-align: left;
  }
  .recipe_wrapper p {
    font-size: 12px;
    font-weight: 400;
    line-height: 15px;
    letter-spacing: 0em;
    text-align: left;
    margin-top: 4px;
  }

  .recipe_details h3 {
    font-size: 12px;
    font-weight: 700;
    line-height: 15px;
    letter-spacing: 0em;
    text-align: left;
    margin-top: 16px;
  }

  li {
    font-size: 12px;
    font-weight: 400;
    line-height: 15px;
    letter-spacing: 0em;
    text-align: left;
    margin-left: 24px;

  }
  .recipe_details {
    padding: 12px;
    padding-bottom: 20px;
  }

</style>