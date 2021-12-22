<template>
  <div class="about-container">
    <ListItem v-bind:item="displayedData" />
    <div class="form-container">
      <div>
        <Form />
      </div>

      <div>
        <router-link class="url" to="/">Back</router-link>
      </div>
    </div>
  </div>
</template>

<script>
import Home from "./Home.vue";
import Header from "../components/Header.vue";
import ListItem from "../components/ListItem.vue";
import Form from "../components/Form.vue";

export default {
  name: "About",
  components: {
    Header,
    Form,
    Home,
    ListItem,
  },
  data() {
    return {
      data: [],
      displayedData: [],
    };
  },
  mounted() {
    const urlParams = new URLSearchParams(window.location.search);
    this.id = urlParams.get("id");
    console.log(this.id);
    fetch(
      "https://api.konimbo.co.il/v1/items?token=9c1a92bf8cefc59e4ec9fa7c53bba0f90dd8b15850bef1062dbf32c5e8fd3a08"
    )
      .then((response) => response.json())
      .then((data) => {
        this.displayedData = data.filter((itemObj) => {
          if (itemObj.id === this.id) return true;
        })[0];
        console.log(this.displayedData);
      });
  },
};
</script>

<style>
.form-container {
  align-items: center;
}

.image {
  display: flex;
  width: 100px;
  height: 100px;
}

.image-container {
  width: 150px;
  height: 130px;
}

.title {
  padding: 5px 10px;
  margin: 5px 10px;
  border: 1px solid black;
  justify-items: center;
}

.item-title {
  border: 1px solid black;
  justify-items: center;
}

.price {
  border: 1px solid black;
}

.about-container {
  /* grid-area: middle; */
  display: flex;
  flex-direction: column;
  justify-items: center;
  align-content: center;
}

.about-container > div {
  margin: 16px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.url {
  padding: auto;
  color: blue;
}
</style>
