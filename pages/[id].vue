<script setup>
// Get the route parameters
const route = useRoute();
const recipeId = route.params.id;
// Fetch the recipe details using the recipe ID
const { data: recipe, status } = await useAsyncApi(`/recipes/${recipeId}`);

// Optionally handle loading state or errors
const isLoading = status.value === 'loading';
const hasError = status.value === 'error';
</script>

<template>
  <div class="p-6">
    <div class="container m-auto">
      <h1 class="text-2xl font-bold mb-4">Recipe Details</h1>

      <div v-if="isLoading" class="text-center">
        <p>Loading recipe...</p>
      </div>

      <div v-if="hasError" class="text-red-600">
        <p>Error loading recipe. Please try again later.</p>
      </div>

      <div v-if="recipe">
        <RecipeCard :recipe="recipe" />
      </div>
    </div>
  </div>
</template>