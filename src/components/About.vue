<template>
  <section class="about py-5 bg-light text-center">
    <div class="container">
      <h2 class="mb-4">Sobre mí</h2>
      <p class="lead">
        ¡Hola! Soy <strong>Carla Cayero</strong>, una desarrolladora entusiasta con pasión por el <strong>Front-End</strong>. 
        Me encanta crear interfaces limpias, modernas y responsivas, siempre enfocándome en la experiencia del usuario.
        Estoy constantemente aprendiendo nuevas tecnologías y buscando formas de mejorar cada detalle visual.
      </p>
    </div>
  </section>
</template>

<script>
export default {
  name: 'About'
}
</script>

<style scoped>
.about {
  background-color: #f1f1f1;
  height: 100vh;
}

h2 {
  font-family: 'Poppins', sans-serif;
  font-weight: 700;
}

p {
  font-family: 'Poppins', sans-serif;
  max-width: 800px;
  margin: 0 auto;
  font-size: 1.2rem;
  line-height: 1.8;
}
</style>
