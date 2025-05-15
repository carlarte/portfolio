<template>
  <div class="projects-container">
    <div class="grid">
      <div
        class="project-card"
        v-for="(project, index) in projects"
        :key="index"
        @click="selectProject(project)"
      >
        <h3>{{ project.name }}</h3>
        <p>{{ project.description }}</p>
        <p>{{ project.tecnologia }}</p>
        <a :href="project.repo" target="_blank" class="repo-link">Ver en GitHub</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      projects: [
        {
          name: 'Puzzle 3x3',
          description: 'Juego de piezas deslizantes',
          tecnologia: 'HTML, CSS, JavaScript',
          repo: 'https://github.com/cep-daw/3x3-puzzle',
          image: '@/assets/projects/carlaa.png'
        },
        {
          name: 'GGGamers',
          description: 'Aplicación web que gestiona eventos de torneos de videojuegos.',
          tecnologia: 'Vue.js y Laravel',
          repo: 'https://github.com/cep-daw/GGGamers',
          image: '@/assets/projects/GGGamers.png'
        },
        {
          name: 'Al-Khaf',
          description: 'Juego RPG de mazmorras.',
          tecnologia: 'HTML, CSS, Java',
          repo: 'https://github.com/cep-daw/role-game',
          image: '@/assets/projects/carlaa.png'
        },
        {
          name: 'ChillGig',
          description: 'Aplicación web que comunica músicos y locales para eventos en directo.',
          tecnologia: 'Vue.js y Laravel',
          repo: 'https://github.com/TheCheetahGirls-3/melodia-conectada',
          image: '@/assets/projects/chillgig.png'
        }
      ]
    };
  },
  methods: {
    selectProject(project) {
      // Emitimos al padre para que se lo pase a Imagen.vue
      this.$emit('update-background', project.image);
    }
  }
};
</script>

<style scoped>
.projects-container {
  padding: 55px 40px;
  background-color: #1e1e1e;
  border-radius: 12px;
  max-width: 600px;
  margin: 0 auto;
  color: white;
}

.grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
  gap: 30px;
}

.project-card {
  background-color: #2c2c2c;
  padding: 33.6px;
  border-radius: 10px;
  cursor: pointer;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.project-card:hover {
  transform: scale(1.03);
  box-shadow: 0 0 20px #38e6ec;
}
.project-card:active {
  box-shadow: 0 0 15px #ffffff, 0 0 50px #38e6ec, 0 0 70px #38e6ec;
}

.project-card h3 {
  font-size: 1.3rem;
  color: #38e6ec;
  margin-bottom: 10px;
  font-weight: bold;
}

.project-card p {
  font-size: 0.95rem;
  margin-bottom: 15px;
}

.repo-link {
  display: inline-block;
  color: #FF5D5D;
  text-decoration: none;
  font-weight: bold;
}

.repo-link:hover {
  text-decoration: underline;
}
</style>
