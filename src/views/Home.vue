<template>
  <div class="container">
    <div class="middle">
      <div class="search-box">
        <label>
          Search Field:
          <input v-on:input="onSearchFieldChange" style="width: 40vw" />
        </label>
      </div>

      <div class="categories">
        <label>
          Categories:
          <select
            class="categoria"
            v-on:input="onSelectChange"
            v-model="selectedCategory"
            style="width: 40vw"
          >
            <option v-for="category in categories" :key="category">
              {{ category }}
            </option>
          </select>
        </label>
      </div>

        <ul class="list">
          <li
            v-for="item in displayedData"
            :key="item.id"
            class="item"
            v-on:click="itemClickHandler(item)"
          >
            <ListItem v-bind:item="item" />
          </li>
        </ul>
    </div>
  </div>
</template>

<script>
import Header from "../components/Header.vue";
import ListItem from "../components/ListItem.vue";
export default {
  name: "Home",
  components: {
    Header,
    ListItem,
  },
  props: {
    title: String,
    price: String,
  },
  data() {
    return {
      data: [],
      count: 0,
      displayedData: [],
      categories: [],
      selectedCategory: "",
    };
  },
  mounted() {
    fetch(
      "https://api.konimbo.co.il/v1/items?token=9c1a92bf8cefc59e4ec9fa7c53bba0f90dd8b15850bef1062dbf32c5e8fd3a08"
    )
      .then((response) => response.json())
      .then((data) => {
        if (Array.isArray(data)) {
          // Filter categories
          this.categories = data.reduce((acc, val) => {
            if (!acc.includes(val.store_category_title)) {
              acc.push(val.store_category_title);
            }
            return acc;
          }, []);
        }
        this.data = data;
        this.displayedData = data;
      });
  },
  methods: {
    onSearchFieldChange(e) {
      this.selectedCategory = "";
      const { value } = e.target;
      const lowerCaseValue = value.toLowerCase();
      this.displayedData = this.data.filter((item) =>
        item.title.toLowerCase().includes(lowerCaseValue)
      );
    },
    onSelectChange(e) {
      const { value } = e.target;
      this.displayedData = this.data.filter(
        (item) => item.store_category_title === value
      );
    },
    itemClickHandler(item) {
      this.$router.push({ path: `/about`, query: { id: item.id } });
    },
  },
};
</script>

<style>
.search-box[input] {
  width: 50px;
}

.search-box,
.categories {
  width: 100%;
  padding: 15px;
  color: #111;
  font-size: 20px;
  height: 64px;
  letter-spacing: 2px;
  text-transform: uppercase;
}

.categories select {
  direction: rtl;
}

.list-div,
.categories,
.search-box {
  background-color: white;
  border: 2px solid black;
  box-shadow: 3px 1px 0px 2px, 0px -1px 0px 2px rgba(0, 0, 0, 0.62);
}

.list-div {
  grid-area: middle;
  font-size: 15px;
  border: 2px solid black;
  background-color: white;
  display: inline;
}

.middle {
  grid-area: middle;
  align-items: center;
}

.list {
  list-style: none;

  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr;
}

.item {
  margin: 16px;
  padding: 6px;
  border: 2px solid black;
  align-items: center;
  display: flex;
  justify-content: center;
  align-items: center;
}

.item-title {
  padding: 10px;
  margin: 10px;
  border: 2px solid yellow;
  outline: 2px solid black;
}

.imagesContainer {
  display: flex;
  list-style: none;
  justify-content: center;
}

.image {
  width: 100px;
  height: 100px;
}

.image-container {
  padding: 5px;
  margin: 10px;
  background-color: white;
  outline: 1px solid yellow;
}
</style>
