<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
  <!-- <counter /> -->
  <Questions />
</template>

<script>
// import Counter from "./components/Counter.vue";
import Questions from "./components/Questions.vue";
export default {
  name: "App",
  components: {
    // Counter,
    Questions,
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
  margin-top: 60px;
}
</style>
