<template>
  <div class="ingredients">
    <h1>All Ingredients</h1>
    <div v-for="ingredient in ingredients">
      <p>{{ ingredient.name }}</p>
      <!-- <img v-bind:src="recipe.image_url" alt /> -->
      <!-- <button>More info</button> -->
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      ingredients: [],
    };
  },
  created: function() {
    axios.get("/api/ingredients").then(response => {
      this.ingredients = response.data;
      console.log(this.ingredients);
    });
  },
  methods: {},
};
</script>