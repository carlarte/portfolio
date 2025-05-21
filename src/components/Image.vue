<template>
  <div>
    <div v-if="projectName !== 'ChillGig'" class="background-image"
      :style="{ backgroundImage: 'url(' + currentImage + ')' }"></div>
    <iframe v-else width="560" height="315" src="https://www.youtube.com/embed/3BCdDngQRXk?si=4nWB9laQtGCDD6gY"
      title="YouTube video player" frameborder="0"
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
      referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
  </div>
</template>

<script>
import carlaImg from '@/assets/projects/carlaa.webp';
export default {
  props: {
    image: String,
    projectName: String
  },
  computed: {
    currentImage() {
      return this.image ? this.image : carlaImg;
    }
  }
};
</script>

<style scoped>
.background-image {
  width: 500px;
  max-width: 500px;
  aspect-ratio: 3 / 4;
  height: auto;
  min-height: 200px;
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