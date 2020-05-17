<template>
  <div class="container">
    <img v-bind:src="recipe.image_url" alt />
    <h2>{{ recipe.name }}</h2>
    <p>Chef: {{ recipe.chef }}</p>
    <p>Description: {{ recipe.description }}</p>
    <!-- ingredients map no longer works -->
    <!-- <ul>Ingredients Needed: {{ recipe.ingredients.map(ingredient => ingredient.name).join(", ") }}</ul> -->
    <p>Prep Time: {{ recipe.prep_time }}</p>
    <p>Directions: {{ recipe.directions }}</p>
    <p>Notes: {{ recipe.notes }}</p>
    <button>
      <router-link to="/recipes">Back to all recipes</router-link>
    </button>
    <p></p>
    <br />
    <button class="btn btn-primary" v-on:click="destroyRecipe(recipe)">Delete recipe</button>
    <br />
  </div>
  <!-- <br />
  <button class="/recipes" v-on:click>Back to all recipes</button>
  <br />-->
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
    this.showRecipe();
  },

  methods: {
    showRecipe: function() {
      axios.get("/api/recipes/" + this.$route.params.id).then(response => {
        console.log("Get one recipes: ", response);
        this.recipe = response.data;
      });
    },
    destroyRecipe: function(recipe) {
      axios.delete("/api/recipes/" + this.$route.params.id).then(response => {
        this.$router.push("/recipes");
      });
    },
  },
};
</script>
