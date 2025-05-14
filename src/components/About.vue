<template>
  <section class="about-container">
    <!-- Parte izquierda: Componente Menu -->
    <div class="about-left">
      <Menu />
    </div>

    <!-- Parte derecha: Imagen -->
    <div class="about-right">
      <Image />
    </div>
  </section>
</template>

<script>
import Image from './Image.vue'
import Menu from './Menu.vue';
export default {
  components: { Image, Menu },
  
}
</script>

<style scoped>
.about-container {
  display: flex;
  height: 100vh; 
}

.about-left {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
  background-color: #161616;
}

.about-right {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
  background-color: #747578;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
}
</style>
