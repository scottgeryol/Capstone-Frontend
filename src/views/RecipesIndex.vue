<template>
  <div class="container">
    <h1>All Recipes</h1>
    <div v-for="recipe in recipes">
      <h2>{{ recipe.name }}</h2>
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
    });
  },
  methods: {},
};
</script>