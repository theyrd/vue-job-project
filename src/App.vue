<template>
  <Header title="Smart Store" />
  <router-view />
</template>

<script>
import Header from "./components/Header.vue";

export default {
  components: {
    Header,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Rubik:ital,wght@1,300&display=swap");

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

@media (max-width: 600px) {
  #app {
    grid-template-areas:
      "header header header header header header"
      "left left left left left left"
      "middle middle middle middle middle middle"
      "right right right right right right"
      "footer footer footer footer footer footer";
  }
}

* {
  box-sizing: border-box;
  font-family: "Rubik", sans-serif;
}

body {
  background-color: #b2b2b2;
}
</style>
