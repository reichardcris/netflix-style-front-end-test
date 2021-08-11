<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
    <Nav />
    <Home />
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import Home from "./components/Home.vue";
import Nav from "./components/Navbar.vue";

export default {
  name: "App",
  components: {
    Home,
    Nav,
  },
};
</script>
