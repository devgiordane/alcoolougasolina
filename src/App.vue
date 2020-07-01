<template>
  <div id="app">
    <Calculadora />
    <Menu></Menu>
  </div>
</template>

<script>
import Calculadora from "./components/Calculadora.vue";
import Menu from "./components/Menu";

export default {
  name: "App",
  components: {
    Calculadora,
    Menu,
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Raleway:wght@400;900&display=swap");
body,
button,
input {
  font-family: "Raleway", sans-serif;
}
body {
  margin: 0;
}
#app {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
</style>
