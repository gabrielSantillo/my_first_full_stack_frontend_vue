<template>
  <div id="app">
    <home-page></home-page>
  </div>
</template>

<script>
import HomePage from "./components/HomePage.vue";

export default {
  name: "App",
  components: {
    HomePage,
  },
};
</script>

<style>
#app {
  margin: 0;
  padding: 0;
  font-family: sans-serif;
  min-height: 100vh;
  place-items: center;
  width: 100%;
}
</style>
