<template>
  <header>
    <h1>{{ title }}</h1>
  </header>
</template>

<script>
export default {
  name: "header",
  props: {
    title: String,
  },
};
</script>

<style>
header {
  grid-area: header;
  background-color: white;
  border: 5px solid black;
  color: #111;
  padding: 1px;
  text-align: center;
  font-size: 20px;
  box-shadow: 3px 1px 0px 2px, 0px -1px 0px 2px rgba(0, 0, 0, 0.62);
  letter-spacing: 2px;
  text-transform: uppercase;
}
</style>
