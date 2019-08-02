<template>
  <div id="app">
    <div id="nav">
      <router-link to="/cars">Cars</router-link> |
      <router-link to="/houses">Houses</router-link> |
      <router-link to="/jobs">Jobs</router-link>
    </div>
    <router-view />
  </div>
</template>
<!-- //cheese -->
<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: black;
    background-color: chocolate;
    font-weight: bolder;

  }

  #nav {
    padding: 30px;
  }

  #nav a {
    font-weight: bold;
    color: black;
  }

  #nav a.router-link-exact-active {
    color: #04b42a;
  }

  img {
    border: solid 2px black;
  }
</style>