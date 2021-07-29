<template>
  <div id="app">
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <a class="navbar-brand" href="#">Where You Wanna Go?</a>
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarNavDropdown"
        aria-controls="navbarNavDropdown"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNavDropdown">
        <ul class="navbar-nav">
          <li class="nav-item active">
            <a class="nav-link" href="/posts">Posts</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="/about">About</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="/posts/new">Create</a>
          </li>
          <li class="nav-item dropdown">
            <a
              class="nav-link dropdown-toggle"
              href="#"
              id="navbarDropdownMenuLink"
              role="button"
              data-bs-toggle="dropdown"
              aria-haspopup="true"
              aria-expanded="false"
            >
              Users!
            </a>
            <div class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
              <li v-if="!isLoggedIn()">
                <a class="dropdown-item" href="/signup">Signup</a>
              </li>
              <li v-if="!isLoggedIn()">
                <a class="dropdown-item" href="/login">Login</a>
              </li>
              <li v-if="isLoggedIn()">
                <a class="dropdown-item" href="/logout">Logout</a>
              </li>
            </div>
          </li>
        </ul>
      </div>
    </nav>
    <!-- <div id="nav">
      <router-link to="/signup">Signup</router-link>
      |
      <router-link to="/login">Login</router-link>
      |
      <router-link to="/">Home</router-link>
      |
      <router-link to="/about">About</router-link>
      |
      <router-link to="/posts">Posts</router-link>
      |
      <router-link to="/logout">Logout</router-link>
      |
      <router-link to="/posts/new">Create</router-link>
    </div> -->
    <router-view />
  </div>
</template>

<style>
body {
  font-family: Copperplate, Copperplate Gothic Light, fantasy !important;
  background-image: url("./assets/trees.png");
  text-align: center;
}
</style>

<script>
export default {
  methods: {
    isLoggedIn: function () {
      if (localStorage.getItem("jwt")) {
        return true;
      } else {
        return false;
      }
    },
    getUserId: function () {
      return localStorage.getItem("user_id");
    },
  },
};
</script>
