<template>
  <Clock />
</template>

<script>
import Clock from "./components/Clock.vue";

export default {
  name: "App",
  components: {
    Clock,
  },
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  box-sizing: border-box;
  color: #2c3e50;
  min-height: 100vh;
  display: grid;
  place-items: center;
}
</style>
