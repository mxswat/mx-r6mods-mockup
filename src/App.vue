<template>
  <div id="app">
    <ModMain></ModMain>
  </div>
</template>

<script>
// import weapons from "./weapons";
import ModMain from "./components/ModMain";
export default {
  name: 'App',
  components: {
    ModMain
  }
}
</script>

<style lang="scss">

body {
  background: #26262b;
  color: white;
}

#app {
  font-family: Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: white;
  margin-top: 60px;
}
</style>
