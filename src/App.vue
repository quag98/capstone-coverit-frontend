<template>
  <div id="app">
    <header>
      
    </header>

    <nav class="navbar navbar-expand-lg navbar-light fixed-top py-3" id="mainNav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> |
      <router-link to="/signup">Signup</router-link> |
      <router-link to="/login">Login</router-link> |
      <router-link to="/logout">Logout</router-link> |
      <router-link to="/songs">Song List</router-link> |
      <router-link to="/favorites">Favorites</router-link> |
    </nav>
    <br>
    <br>
    <br>
    <router-view />

  <footer class="bg-light py-5">
       <div class="container">
                <div class="small text-center text-muted">
                    Copyright &copy;
                    <!-- This script automatically adds the current year to your website footer-->
                    <!-- (credit: https://updateyourfooter.com/)-->
                    <!-- <script>
                        document.write(new Date().getFullYear());
                    </script> -->
                    - Company Name
                </div>
            </div>
  </footer>

  </div>
</template>

<style>
#app {
  position: relative;
  min-height: 120vh;
}

.content-wrap {
  padding-bottom: 2.5rem; /* Footer height */
}

.bg-light.py-5 {
  position: absolute;
  bottom: 0;
  width: 100%;
  height: 2.5rem;
}
</style>
