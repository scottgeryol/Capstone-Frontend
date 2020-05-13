<template>
  <div class="ingredient_users">
    <h1>Welcome to your Pantry!</h1>
    <div v-for="ingredient_user in ingredient_users">
      <p>{{ ingredient_user.ingredient.name }}</p>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      ingredient_users: [],
    };
  },
  created: function() {
    axios.get("/api/ingredient_users").then(response => {
      this.ingredient_users = response.data;
      console.log(this.ingredient_users);
    });
  },
  methods: {},
};
</script>