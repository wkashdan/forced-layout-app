<template>
  <div class="image-grid">
    <div v-for="i in numOfImages" :key="i">
      <img ref="randomImage" :src="generateImageUrl()" class="image-grid-item" />
    </div>
  </div>
</template>

<script>
const NUMBER_OF_IMAGES = 1200;
const IMAGE_WIDTH = 100;
const IMAGE_HEIGHT = 100;

export default {
  name: 'App',
  data() {
    return {
      numOfImages: NUMBER_OF_IMAGES,
      nextImageToChange: 0,
    }
  },

  mounted() {
    // after initial render start changing image sizes
    setTimeout(() => {
      this.startChangingImages();
    }, 1000);
  },

  methods: {
    generateImageUrl() {
      return `https://picsum.photos/${IMAGE_WIDTH}/${IMAGE_HEIGHT}?random=${Math.random()}`;
    },

    startChangingImages() {
      setInterval(() => {
        const imgEl = this.$refs.randomImage[this.nextImageToChange];
        const size = Math.round(Math.random() * 100);
        imgEl.height = size;
        imgEl.weight = size;
        this.nextImageToChange = (this.nextImageToChange + 1) % this.numOfImages;
        console.log('Bounding client rect: ', imgEl.getBoundingClientRect());
      }, 100);
    }
  }
}
</script>

<style>
body {
  padding: 0;
  margin: 0;
}
</style>

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
