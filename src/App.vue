<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/AddPosts">Add Posts</router-link> |
      <router-link to="/editPost">Edit Posts</router-link>
    </div>
    <router-view/>
    <div class ="footer">
    <a href="https://github.com/jahali25/BlogUpdated" target="_blank">
      <img src="/images/GitHub-Mark-120px-plus.png">
    </a>
  </div>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
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
