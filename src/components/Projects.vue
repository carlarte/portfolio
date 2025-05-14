<template>
  <div>
    <h2>Proyectos</h2>
    <div class="project-card" v-for="(project, index) in projects" :key="index">
      <h3>{{ project.name }}</h3>
      <p>{{ project.description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Projects',
  data() {
    return {
      projects: [
        { name: 'Portfolio', description: 'Mi portfolio personal desarrollado con Vue.js.' },
        { name: 'E-commerce', description: 'Tienda en línea con carrito de compras.' },
        { name: 'Blog', description: 'Blog personal con sistema de comentarios.' },
      ],
    };
  },
};
</script>

<style scoped>
.project-card {
  background-color: #2c2c2c;
  padding: 15px;
  margin: 10px 0;
  border-radius: 5px;
}
</style>