<template>
  <div id="app">
    <div id="nav">
      <router-link to="/" class="text-gray-800">Home</router-link> |
      <router-link to="/covid" class="text-gray-800">Data Covid</router-link>
    </div>
    <router-view/>
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
  padding: 25px;
  background-color:darkturquoise;
  width: 1349px;
}

#nav a {
  font-weight: bold;
}

#nav a.router-link-exact-active {
  color:darkgreen
}
</style>