<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <AxiosComponent />
  </div>
</template>

<script>
import AxiosComponent from "@/components/AxiosComponent.vue";

export default {
  name: "App",
  components: {
    AxiosComponent,
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
