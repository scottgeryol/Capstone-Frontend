<template>
  <div class="ingredients">
    <a href="#">
      <strong>All Ingredients</strong>
      <br />
    </a>

    <div class="row aln-center">
      <div v-for="ingredient in ingredients" class="col-4 col-6-medium col-12-small">
        <!-- Feature -->
        <section>
          <a href="#" class="image featured">
            <img v-bind:src="ingredient.image_url" alt class="ingredient-image" />
          </a>
          <header>
            <h3>{{ ingredient.name }}</h3>
            <a href="/ingredient_users" class="button icon solid fa-file">Add to your pantry!</a>
          </header>
          <!-- <p>
            This is
            <strong>Strongly Typed</strong>, a free, fully responsive site template
            by
            <a
              href="http://html5up.net"
            >HTML5 UP</a>. Free for personal and commercial use under the
            <a
              href="http://html5up.net/license"
            >CCA 3.0 license</a>.
          </p>-->
        </section>
      </div>
    </div>
    <!-- <div v-for="ingredient in ingredients">
      <img v-bind:src="ingredient.image_url" alt />
      <li>{{ ingredient.name }}</li>
      <p>{{ ingredient.price }}</p>
      <!-- <img v-bind:src="recipe.image_url" alt /> -->
      <!-- <button>More info</button> -->
      <!-- <li>
        <a href="/ingredient_users" class="button icon solid fa-file">Add to your pantry!</a>
      </li> -->
    </div> 
  </div>
</template>

<style>
.ingredient-image {
  height: 400px;
  object-fit: cover;
}
</style>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      ingredients: [],
      price: [],
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