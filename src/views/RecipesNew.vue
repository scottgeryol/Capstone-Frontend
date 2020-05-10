<template>
  <div class="container">
    <img v-if="status" v-bind:src="`https://http.cat/${status}`" alt />
    <h1>New Recipe</h1>
    <form v-on:submit.prevent="createRecipe()">
      <ul>
        <li class="text-danger" v-for="error in errors">{{ error }}</li>
      </ul>Name:
      <input type="text" v-model="newRecipeName" />
      Description:
      <input type="text" v-model="newRecipeDescription" />
      Directions:
      <input type="text" v-model="newRecipeDirections" />
      Prep Time:
      <input type="text" v-model="newRecipePrepTime" />
      Notes:
      <input type="text" v-model="newRecipeNotes" />
      Image:
      <input type="text" v-model="newRecipeImageUrl" />
      <input type="submit" value="Create" />
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      newRecipeName: "",
      newRecipeDescription: "",
      newRecipeDirections: "",
      newRecipePrepTime: "",
      newRecipeNotes: "",
      newRecipeImageUrl: "",
      errors: [],
      status: "",
    };
  },
  // created: function() {},
  methods: {
    createPhoto: function() {
      var params = {
        name: this.newRecipeName,
        description: this.newRecipeDescription,
        directions: this.newRecipeDirections,
        prep_time: this.newRecipePrepTime,
        notes: this.newRecipeNotes,
        image_url: this.newRecipeImageUrl,
      };
      axios
        .post("/api/recipes", params)
        .then(response => {
          this.$router.push("/recipes");
        })
        .catch(error => {
          console.log(error.response);
          this.errors = error.response.data.errors;
          this.status = error.response.status;
        });
    },
  },
};
</script>