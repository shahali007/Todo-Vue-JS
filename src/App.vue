<template>
  <div id="app">
    <Header/>
    <router-view/>
  </div>
</template>

<script>
import Header from "./components/common/Header";
export default {
  name: "app",
  components: {
    Header
  },
  data() {
    return {};
  }
};
</script>

<style>
body {
  padding-top: 100px;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: auto;
}

.not-found {
  margin-top: 100px;
}
</style>
