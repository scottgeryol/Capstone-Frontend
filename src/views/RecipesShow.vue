<template>
  <div class="container">
    <img v-bind:src="recipe.image_url" class="recipe-image" alt />
    <br />
    <h2>{{ recipe.name }}</h2>
    <div>
      <strong>Chef:</strong>
      {{ recipe.chef }}
    </div>
    <br />
    <div>
      <strong>Description:</strong>
      {{ recipe.description }}
    </div>
    <br />
    <strong>Ingredients:</strong>
    <br />
    <div v-for="ingredient in recipe.ingredients">{{ ingredient.name }}</div>
    <br />
    <div>
      <strong>Prep Time:</strong>
      {{ recipe.prep_time }}
    </div>
    <br />
    <div>
      <strong>Directions:</strong>
      {{ recipe.directions }}
    </div>
    <br />
    <div>
      <strong>Notes:</strong>
      {{ recipe.notes }}
    </div>
    <br />
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

<style>
.recipe-image {
  height: 375px;
  margin-left: auto;
  margin-right: auto;
  object-fit: cover;
}
</style>

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
