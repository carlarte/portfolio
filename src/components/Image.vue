<template>
  <div class="background-image" :style="{ backgroundImage: 'url(' + image + ')' }"></div>
</template>

<script>
export default {
  props: {
    image: String
  }
};
</script>

<style scoped>
.background-image {
  width: 100%;
  height: 100vh;
  background-size: cover;
  background-position: center;
  transition: background-image 0.6s ease-in-out;
}
</style>