<template>
  <div class="background-image" :style="{ backgroundImage: 'url(' + currentImage + ')' }"></div>
</template>

<script>
import carlaImg from '@/assets/projects/carlaa.png';
export default {
  props: {
    image: String
  },
  computed: {
    currentImage() {
      return this.image || carlaImg;
    }
  }
};
</script>

<style scoped>
.background-image {
  width: 70%;
  height: 100%;
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
  transition: background-image 0.6s ease-in-out;
}
@media (max-width: 1000px) {
  .background-image {
    width: 100%;
    height: 100%;
  }
}
</style>