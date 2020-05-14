<template>
  <div id="app">
    <!-- <div id="nav">
      <router-link to="/">Home</router-link>|
      <router-link to="/about">About</router-link>|
      <router-link to="/recipes">All Recipes</router-link>|
      <router-link to="/recipes/new">Create a Recipe</router-link>|
      <router-link to="/ingredients">All Ingredients</router-link>|
      <router-link to="/ingredient_users">My Pantry</router-link>|
    </div>-->

    <!-- Header -->
    <section id="header">
      <div class="container">
        <!-- Logo -->
        <h1 id="logo">
          <a href="index.html">Pantry Pulls</a>
        </h1>
        <p>A new way to find recipes!</p>

        <!-- Nav -->
        <nav id="nav">
          <ul>
            <li>
              <a class="icon solid fa-home" href="/">
                <span>Home</span>
              </a>
            </li>
            <li>
              <a href="#" class="icon fa-chart-bar">
                <span>Dropdown</span>
              </a>
              <ul>
                <li>
                  <a href="/RecipesIndex">Recipes</a>
                </li>
                <li>
                  <a href="#">Magna phasellus</a>
                </li>
                <li>
                  <a href="#">Etiam dolore nisl</a>
                </li>
                <li>
                  <a href="#">Phasellus consequat</a>
                  <ul>
                    <li>
                      <a href="#">Magna phasellus</a>
                    </li>
                    <li>
                      <a href="#">Etiam dolore nisl</a>
                    </li>
                    <li>
                      <a href="#">Phasellus consequat</a>
                    </li>
                  </ul>
                </li>
                <li>
                  <a href="#">Veroeros feugiat</a>
                </li>
              </ul>
            </li>
            <li>
              <a class="icon solid fa-cog" href="/about">
                <span>About</span>
              </a>
            </li>
            <li>
              <a class="icon solid fa-cog" href="../views/RecipesIndex.vue">
                <span>Recipes</span>
              </a>
            </li>
            <li>
              <a class="icon solid fa-retweet" href="/login">
                <span>Login</span>
              </a>
            </li>
            <li>
              <a class="icon solid fa-sitemap" href="/logout">
                <span>Logout</span>
              </a>
            </li>
          </ul>
        </nav>
      </div>
    </section>

    <router-view />

    <!-- Footer -->
    <section id="footer">
      <div class="container">
        <header>
          <h2>
            Questions or comments?
            <strong>Get in touch:</strong>
          </h2>
        </header>
        <div class="row">
          <div class="col-6 col-12-medium">
            <section>
              <form method="post" action="#">
                <div class="row gtr-50">
                  <div class="col-6 col-12-small">
                    <input name="name" placeholder="Name" type="text" />
                  </div>
                  <div class="col-6 col-12-small">
                    <input name="email" placeholder="Email" type="text" />
                  </div>
                  <div class="col-12">
                    <textarea name="message" placeholder="Message"></textarea>
                  </div>
                  <div class="col-12">
                    <a
                      href="#"
                      class="form-button-submit button icon solid fa-envelope"
                    >Send Message</a>
                  </div>
                </div>
              </form>
            </section>
          </div>
          <div class="col-6 col-12-medium">
            <section>
              <p>
                Erat lorem ipsum veroeros consequat magna tempus lorem ipsum consequat Phaselamet mollis tortor
                congue. Sed quis mauris sit amet magna accumsan tristique. Curabitur leo nibh, rutrum eu malesuada.
              </p>
              <div class="row">
                <div class="col-6 col-12-small">
                  <ul class="icons">
                    <li class="icon solid fa-home">
                      1234 Somewhere Road
                      <br />Nashville, TN 00000
                      <br />USA
                    </li>
                    <li class="icon solid fa-phone">(000) 000-0000</li>
                    <li class="icon solid fa-envelope">
                      <a href="#">info@untitled.tld</a>
                    </li>
                  </ul>
                </div>
                <div class="col-6 col-12-small">
                  <ul class="icons">
                    <li class="icon brands fa-twitter">
                      <a href="#">@untitled</a>
                    </li>
                    <li class="icon brands fa-instagram">
                      <a href="#">instagram.com/untitled</a>
                    </li>
                    <li class="icon brands fa-dribbble">
                      <a href="#">dribbble.com/untitled</a>
                    </li>
                    <li class="icon brands fa-facebook-f">
                      <a href="#">facebook.com/untitled</a>
                    </li>
                  </ul>
                </div>
              </div>
            </section>
          </div>
        </div>
      </div>
      <div id="copyright" class="container">
        <ul class="links">
          <li>&copy; Untitled. All rights reserved.</li>
          <li>
            Design:
            <a href="http://html5up.net">HTML5 UP</a>
          </li>
        </ul>
      </div>
    </section>
  </div>
</template>

<style>
</script>