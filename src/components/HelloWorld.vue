<template>
  <div class="image-grid">
    <div v-for="i in numOfImages" :key="i">
      <img :src="generateImageUrl()" class="image-grid-item" />
    </div>
  </div>
</template>

<script>
const NUMBER_OF_IMAGES = 20;
const IMAGE_WIDTH = 400;
const IMAGE_HEIGHT = 400;

export default {
  name: 'HelloWorld',
  data() {
    return {
      numOfImages: NUMBER_OF_IMAGES,
    }
  },
  methods: {
    generateImageUrl() {
      return `https://picsum.photos/${IMAGE_WIDTH}/${IMAGE_HEIGHT}?random=${Math.random()}`;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.image-grid {
  background-color: black;
  display: flex;
  flex-wrap: wrap;
  width: 100%;
}

.image-grid-item {
  flex: 1 0 auto;
  opacity: .2;
}
</style>
