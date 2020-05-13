<template>
  <div class="container">
    <img v-if="status" v-bind:src="`https://http.cat/${status}`" alt />
    <h1>New Recipe</h1>
    <form v-on:submit.prevent="createRecipe()">
      <ul>
        <li class="text-danger" v-for="error in errors">{{ error }}</li>
      </ul>Name:
      <input type="string" v-model="newRecipeName" />
      Chef:
      <input type="string" v-model="newRecipeChef" />
      Description:
      <input type="string" v-model="newRecipeDescription" />
      Directions:
      <input type="string" v-model="newRecipeDirections" />
      Prep Time:
      <input type="integer" v-model="newRecipePrepTime" />
      Notes:
      <input type="string" v-model="newRecipeNotes" />
      Image Url:
      <input type="string" v-model="newRecipeImageUrl" />
      <input type="submit" value="New" />
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      newRecipeName: "",
      newRecipeChef: "",
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
    createRecipe: function() {
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