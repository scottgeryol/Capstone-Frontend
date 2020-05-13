<template>
  <h1>Welcome to your Pantry!</h1>
  <div v-else-if="ingredient in ingredient_user">
    <p>{{ ingredient_user.ingredient_id }}</p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      ingredient_user: [],
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