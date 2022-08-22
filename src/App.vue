<template>
  <div id="app" class="bg-gray-900  min-h-screen">
    <nav>
      <router-link to="/">Formulario</router-link> |
      <router-link to="/list">lista</router-link>
    </nav>
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

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #ffff;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
