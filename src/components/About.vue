<template>
  <section class="about-container" id="about">
    <!-- Parte izquierda: Componente Menu -->
    <div class="about-left">
      <Menu @update-background="background = $event" @update-project-name="selectedProjectName = $event"/>
    </div>

    <!-- Parte derecha: Imagen -->
    <div class="about-right">
      <Image :image="background" :projectName="selectedProjectName"/>
    </div>
  </section>
</template>

<script>
import Image from './Image.vue'
import Menu from './Menu.vue';
export default {
  data() {
    return {
      background: '',
      selectedProjectName: '',
    };
  },
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
  background-color: #161616;
  min-width: 300px;
  min-height: 400px;
  height: 100%;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
}
@media (max-width: 1000px) {
  .about-right {
    display: none;
  }
}
</style>
