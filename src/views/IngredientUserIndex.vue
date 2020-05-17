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
              <h3>{{ ingredient_user.ingredient.name }}</h3>
              <header>
                <!-- <h3 v-for="ingredient in ingredient_users.ingredients">{{ ingredient }}</h3> -->
              </header>
              <!-- <p>
                This is
                <strong>Strongly Typed</strong>
                , a free, fully responsive site template by
                <a
                  href="http://html5up.net"
                >HTML5 UP</a>
                . Free for personal and commercial use under the
                <a
                  href="http://html5up.net/license"
                >CCA 3.0 license</a>
                .
              </p>-->
            </div>
          </div>
          <div class="col-12">
            <ul class="actions">
              <li>
                <a href="#" class="button icon solid fa-file">Tell Me More</a>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <!-- <h1>Welcome to your Pantry!</h1> -->
    <!-- <div v-for="ingredient_user in ingredient_users"> -->
    <!-- <p>{{ ingredient_user.ingredient.name }}</p> -->
    <!-- </div> -->
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      ingredient_users: [],
      ingredients: [],
      name: "",
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
        input_name: this.name,
      };
      var myVariable = 0;
      axios
        .post("/api/recipes", params)
        .then(response => {
          this.$router.push("/ingredient_user");
        })
        .catch(error => {
          this.errors = error.response.data.errors;
          this.status = error.response.status;
        });
    },
  },
};
</script>