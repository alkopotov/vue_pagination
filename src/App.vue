<template>
  
  <h1>Recipes</h1>
  <pagination-elem
    :current="currentPage" 
    :maxPages="computedNumberOfPages" 
    @incrPage="incrCurrentPage" 
    @decrPage="decrCurrentPage" 
    @setPage="setCurrentPage"
  ></pagination-elem>
  <recipes-list :recipes="computedRecipesOnPage"></recipes-list>
 
</template>
 
<script setup>
  import { computed, onMounted, reactive, ref } from 'vue';
  import axios from 'axios';
  import PaginationElem from './components/PaginationElem.vue';
  import RecipesList from './components/RecipesList.vue';
 
 
    let recipes = ref([]);
 
    let currentPage = ref(1);
 
    let maxRecipesOnPage = ref(6);
 
    let computedNumberOfPages = computed(() => {
      return Math.ceil(recipes.value.length / maxRecipesOnPage.value);
    })
    
    let computedRecipesOnPage = computed(() => {
      let firstElem = (currentPage.value - 1) * maxRecipesOnPage.value;
      return recipes.value.slice(firstElem, firstElem + maxRecipesOnPage.value)
    })
    
    function setCurrentPage(page) {
      currentPage.value = page
    }

    function incrCurrentPage() {
      if (currentPage.value < computedNumberOfPages.value) {
        currentPage.value++
      }
    }

    function decrCurrentPage() {
      if (currentPage.value > 1) {
        currentPage.value--
      }
    }

    onMounted(async () => {
      try {
        let res = await axios.get('https://dummyjson.com/recipes')
        recipes.value = res.data.recipes
      }
      catch(e) {
        console.log(e);
      }
 
    })
 
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');
 * {
  font-family: "Inter", sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
 }

 h1 {
  font-size: 48px;
  font-weight: 400;
  line-height: 58px;
  letter-spacing: 0em;
  text-align: center;
  margin-top: 40px;
 }
</style>