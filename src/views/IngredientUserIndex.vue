<template>
  <div class="ingredient_users">
    <!-- Features -->
    <section id="features">
      <div class="container">
        <header>
          <h2>
            <strong>Welcome to your pantry!</strong>
          </h2>
        </header>
        <div class="row aln-center">
          <div class="col-4 col-6-medium col-12-small">
            <!-- Feature -->
            <div v-for="ingredient_user in ingredient_users">
              <h3
                v-on:click="query=ingredient_user.ingredient.name"
              >{{ ingredient_user.ingredient.name }}</h3>
            </div>
            <div class="form-group">
              <strong>Search for a new recipe!</strong>
              <br />
              <form v-on:submit.prevent="search()">
                <input type="text" class="form-control" v-model="query" />
                <br />
                <input type="submit" class="btn btn-primary" value="Search" />
              </form>
              <br />
              <div v-for="recipe in recipesearch">
                <h4>
                  <a v-bind:href="recipe.recipe.url" target="_blank">{{ recipe.recipe.label }}</a>
                </h4>
                <img v-bind:src="recipe.recipe.image" alt />
                <strong>Ingredients:</strong>
                <div v-for="ingredientLine in recipe.recipe.ingredientLines">{{ ingredientLine }}</div>
                <br />
                <strong>Calories:</strong>
                <p>{{ recipe.recipe.calories }}</p>
                <strong>Diet & Allergy:</strong>
                <div v-for="healthLabel in recipe.recipe.healthLabels">{{ healthLabel }}</div>
                <br />
              </div>
            </div>
          </div>
          <div class="col-12">
            <ul class="actions">
              <li>
                <a href="/recipes" class="button icon solid fa-file">Lets get cooking!</a>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      ingredient_users: [],
      ingredient_user: {},
      ingredients: [],
      name: "",
      recipesearch: [],
      query: "",
    };
  },
  created: function() {
    axios.get("/api/ingredient_users").then(response => {
      this.ingredient_users = response.data;
      console.log(this.ingredient_users);
    });
  },
  methods: {
    submit: function() {
      var params = {
        input_ingredient_id: this.ingredient_id,
      };
      var myVariable = 0;
      axios
        .post("/api/ingredient_users", params)
        .then(response => {
          this.$router.push("/ingredient_user");
        })
        .catch(error => {
          this.errors = error.response.data.errors;
          this.status = error.response.status;
        });
    },
    search: function() {
      axios.get("/api/recipesearch?query=" + this.query).then(response => {
        this.recipesearch = response.data.hits;
        console.log(this.recipesearch);
      });
    },
  },
};
</script>