<template>
  <div id="app ">
    <br />
    <div class="container">
      <games />
      <br />
    </div>
    <br />
  </div>
</template>

<script>
import games from "@/components/games";

export default {
  name: "App",
  components: {
    games,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
  background-color: rgb(20, 17, 17);
}
</style>
