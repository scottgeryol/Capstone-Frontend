<template>
  <div class="recipes">
    <!-- Features -->
    <section id="features">
      <div class="container">
        <header>
          <h2>
            <strong>All Recipes</strong>
            <p></p>
            <p>Try a new recipe today!</p>
          </h2>
        </header>
        <div class="row aln-center">
          <div class="col-4 col-6-medium col-12-small">
            <!-- Feature -->
            <section v-for="recipe in recipes">
              <a href="#" class="image featured">
                <img v-bind:src="recipe.image_url" alt />
                <!-- <img src="images/pic01.jpg" alt /> -->
              </a>
              <header>
                <h3>{{ recipe.name }}</h3>
              </header>
              <p>{{ recipe.description }}</p>
              <div>
                <strong>Chef:</strong>
                <p>{{ recipe.chef }}</p>
              </div>
              <div>
                <strong>Ingredients Needed:</strong>
                <ul>{{ recipe.ingredients.map(ingredient => ingredient.name).join(", ") }}</ul>
              </div>

              <router-link v-bind:to="`/recipes/${recipe.id}`">View Recipe!</router-link>
            </section>
          </div>
          <div class="col-12">
            <ul class="actions">
              <li>
                <!-- <a href="#" class="button icon solid fa-file">Tell Me More</a> -->
              </li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <!-- <h1>All Recipes</h1>
    <div v-for="recipe in recipes">
      <h2>{{ recipe.name }}</h2>
      <p>{{ recipe.description }}</p>
      <p>Ingredients Needed: {{ recipe.ingredients.map(ingredient => ingredient.name).join(", ") }}</p>
      <p>Chef: {{ recipe.chef }}</p>
      <img v-bind:src="recipe.image_url" alt />
      <router-link v-bind:to="`/recipes/${recipe.id}`">View Recipe!</router-link>
    </div>-->
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








































