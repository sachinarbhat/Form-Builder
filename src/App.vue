<template>
  <div class="container mt-2" id="app">
  <span class="h5"><img src="https://upload.wikimedia.org/wikipedia/commons/7/7d/Abawikilogo.png" alt="ABA" width="7%"/> Admin Utility Tool</span>
  
  <hr/>
    <router-view/>
  </div>
</template>
<script>

export default {
  name: "App",
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
