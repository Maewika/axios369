<template>
  <div id="app">
    <Anime/>
  </div>
</template>

<script>
import Anime from "./components/Anime"
export default {
  name: "App",
  components: {
   Anime,
  },
};
</script>

<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: tomato;
  margin-top: 0px;
}
body { 
  background-image: url("./assets/2.jpg"); 
  background-attachment: fixed;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}
</style>