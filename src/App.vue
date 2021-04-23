<template>
  <div id="app">
   
    <Navbar/>
    <Sidebar/>

    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> |
      <router-link to="/pkm-team">Criar Time</router-link> |
      <router-link to="/nature-pkm">Nature Pokemon</router-link>
    </div>
    <router-view />
  </div>
</template>

<script>

import Navbar from "@/components/Navbar.vue";
import Sidebar from "@/components/Sidebar.vue";

export default {
  name: "Home",
  components: {
    Navbar,
    Sidebar
  }
}

</script>

<style>
#img_logo {
  height: 20px;
}

#tittleNav{
  font-size: smaller;
}

#mynav {
  background-color:#42f58d;
}

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

#sidebar-1 p {
  color: #fcba03;
}

</style>
