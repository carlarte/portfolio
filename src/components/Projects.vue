<template>
  <div class="projects-scroll-container" ref="scrollContainer">
    <div class="projects-scroll-content">
      <div class="grid">
        <template v-for="(project, index) in projects" :key="index">
          <div class="project-card hoverable" @click="selectProject(project)" ref="sections">
            <h3>{{ project.name }}</h3>
            <p>{{ project.description }}</p>
            <p>{{ project.tecnologia }}</p>
            <div class="github">
              <a :href="project.repo" target="_blank" class="repo-link" @click.stop>GitHub</a>
              <a v-if="project.link" :href="project.link" target="_blank" class="web-link" @click.stop>Web</a>
            </div>
          </div>
        </template>
      </div>
    </div>
  </div>
</template>

<script>
import { animate, onScroll } from 'animejs';
import role from '@/assets/projects/role.png';
import puzzleImg from '@/assets/projects/puzzle.png';
// import chillgigImg from '@/assets/projects/chillgig.png';
import gggamersImg from '@/assets/projects/gggamers.png';
export default {
  data() {
    return {
      projects: [
        {
          name: 'Puzzle 3x3',
          description: 'Juego de piezas deslizantes',
          tecnologia: 'HTML, CSS, JavaScript',
          repo: 'https://github.com/cep-daw/3x3-puzzle',
          image: puzzleImg,
          link: 'https://puzzle.carlacayero.me/'
        },
        {
          name: 'GGGamers',
          description: 'Aplicación web que gestiona eventos de torneos de videojuegos.',
          tecnologia: 'Vue.js y Laravel',
          repo: 'https://github.com/cep-daw/GGGamers',
          image: gggamersImg,
          link: 'https://gggamers.carlacayero.me/'
        },
        {
          name: 'Al-Khaf',
          description: 'Juego RPG de mazmorras.',
          tecnologia: 'HTML, CSS, Java',
          repo: 'https://github.com/cep-daw/role-game',
          image: role
        },
        {
          name: 'ChillGig',
          description: 'Aplicación web que comunica músicos y locales para eventos en directo.',
          tecnologia: 'Vue.js y Laravel',
          repo: 'https://github.com/TheCheetahGirls-3/melodia-conectada',
          // image: chillgigImg
        }
      ]
    };
  },
  methods: {
    selectProject(project) {
      this.$emit('update-background', project.image);
      this.$emit('update-project-name', project.name);
    }
  },
  mounted() {
    this.$nextTick(() => {
      const sections = this.$refs.sections;
      const container = this.$refs.scrollContainer;
      const sectionArray = Array.isArray(sections) ? sections : [sections];
      sectionArray.forEach(section => {
        animate(section, {
          opacity: [0, 1],
          translateY: [50, 0],
          duration: 1000,
          easing: 'easeOutExpo',
          autoplay: onScroll({
            target: section,
            container: container,
            threshold: 0.5
          })
        });
      });
    });
  }
};
</script>

<style scoped>
.project-link {
  text-decoration: none;
  color: inherit;
  display: block;
}

.projects-scroll-container {
  max-height: 685px;
  width: 100%;
  max-width: 600px;
  overflow-y: auto;
  margin: 0 auto;
  background-color: #161616;
  color: white;
  border-radius: 10px;
  padding: 10px;
  scrollbar-width: none;
  -ms-overflow-style: none;
}

.projects-scroll-container::-webkit-scrollbar {
  display: none;
}

.projects-scroll-content {
  max-width: 600px;
  display: flex;
  flex-direction: column;
  gap: 30px;
  padding: 20px;
  background-color: #1e1e1e;
  border-radius: 10px;
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
  opacity: 0;
  transform: translateY(50px);
  transition: opacity 0.3s ease, transform 0.3s ease;
  display: flex;
  flex-direction: column;
}

.project-card.hoverable:hover {
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

.repo-link:hover,
.web-link:hover {
  /* Cambia el subrayado por un efecto de fondo y color */
  background: linear-gradient(90deg, #38e6ec 0%, #FF5D5D 100%);
  color: #fff;
  border-radius: 5px;
  padding: 2px 8px;
  box-shadow: 0 2px 10px rgba(56,230,236,0.2);
  transform: translateY(-2px) scale(1.07) rotate(-2deg);
  transition: all 0.2s;
  text-decoration: none;
}

.web-link {
  display: inline-block;
  color: #38e6ec;
  text-decoration: none;
  font-weight: bold;
}
.github {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: auto;
}
</style>