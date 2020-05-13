<template>
  <div class="container">
    <img v-bind:src="recipe.image_url" alt />
    <h2>Name: {{ recipe.name }}</h2>
    <p>Description: {{ recipe.description }}</p>
    <p>Ingredients: {{ recipe.ingredients.map(ingredient => ingredient.name).join(", ") }}</p>
    <p>Prep Time: {{ recipe.prep_time }}</p>
    <p>Directions: {{ recipe.directions }}</p>
    <p>Notes: {{ recipe.notes }}</p>
    <router-link to="/recipes">Back to all recipes</router-link>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      recipe: [],
    };
  },
  created: function() {
    axios.get("/api/recipes/" + this.$route.params.id).then(response => {
      this.recipe = response.data;
    });
  },
  methods: {},
};
</script>
