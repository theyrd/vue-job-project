<template>
  <div>
    <div class="item-title"><b>{{ item.title }} - Price: {{ item.price }}</b></div>

    <div class="image-container">
      <img :src="item.images?.[this.curImage]?.url" alt="Missing picture" class="image" />
      <div>
        <button v-on:click="handleBackward" :disabled="this.curImage === 0">
          &lt;
        </button>
        <button
          v-on:click="handleForward"
          :disabled="this.curImage === item.images?.length - 1"
        >
          >
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ListItem",
  props: {
    item: {},
  },
  data() {
    return {
      curImage: 0,
    };
  },
  methods: {
    handleBackward(e) {
      e.stopPropagation();
      this.curImage -= 1;
    },
    handleForward(e) {
      e.stopPropagation();
      this.curImage += 1;
    },
  },
};
</script>

<style>
.image-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
