<template>
  <div class="recipes">
    <h1>All Recipes</h1>
    <div v-for="recipe in recipes">
      <h2>{{ recipe.name }}</h2>
      <p>{{ recipe.description }}</p>
      <img v-bind:src="recipe.image_url" alt />
      <button>More info</button>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      recipes: [],
    };
  },
  created: function() {
    axios.get("/api/recipes").then(response => {
      this.recipes = response.data;
      console.log(this.recipes);
    });
  },
  methods: {},
};
</script>