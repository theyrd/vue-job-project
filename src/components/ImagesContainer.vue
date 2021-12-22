<template>
  <div>
    <button :v-on:click="changeImage('back')">Back</button>
    <div class="image-container">
      <img :src="currentImage?.url" class="image" />
    </div>
    <button :v-on:click="changeImage('next')">Next</button>
  </div>
</template>

<script>
export default {
  name: "ImagesContainer",
  data() {
    currentImage: {
    }
  },
  props: {
    images: Array,
  },
  mounted() {
    this.currentImage = this.images[0];
  },
  methods: {
    /**
     * diretcion - 'next' | 'back
     */
    changeImage(direction) {},
    onClick() {
      console.log("click");
    },
  },
};
</script>

<style>
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
  background-color: black;
  outline: 1px solid yellow;
}
</style>
