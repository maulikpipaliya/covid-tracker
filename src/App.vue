<template>
  <div id="app">
    <HeaderHome />
    <MainContainer />
  </div>
</template>

<script>
import HeaderHome from "./components/HeaderHome.vue";
import MainContainer from "./components/MainContainer.vue";

export default {
  name: "App",
  components: {
    HeaderHome,
    MainContainer,
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
}
</style>
