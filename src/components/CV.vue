<template>
  <div class="scroll-container">
    <div class="scroll-content">
      <div
        v-for="(item, index) in timeline"
        :key="index"
        class="scroll-section"
        ref="sections"
      >
        <h2 class="date">{{ item.date }}</h2>
        <p class="description">{{ item.description }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import { animate, onScroll } from 'animejs';

export default {
  data() {
    return {
      timeline: [
        { date: "2020", description: "Comencé mis estudios en Desarrollo Web." },
        { date: "2021", description: "Realicé prácticas en Empresa XYZ." },
        { date: "2022", description: "Trabajé como Desarrollador Frontend Junior." },
        { date: "2023", description: "Me especialicé en Vue.js y tecnologías modernas." },
        { date: "2020", description: "Comencé mis estudios en Desarrollo Web." },
        { date: "2021", description: "Realicé prácticas en Empresa XYZ." },
        { date: "2022", description: "Trabajé como Desarrollador Frontend Junior." },
        { date: "2023", description: "Me especialicé en Vue.js y tecnologías modernas." },
        { date: "2020", description: "Comencé mis estudios en Desarrollo Web." },
        { date: "2021", description: "Realicé prácticas en Empresa XYZ." },
        { date: "2022", description: "Trabajé como Desarrollador Frontend Junior." },
        { date: "2023", description: "Me especialicé en Vue.js y tecnologías modernas." },
      ],
    };
  },
  mounted() {
    const sections = this.$refs.sections;
    const sectionArray = Array.isArray(sections) ? sections : [sections];

    sectionArray.forEach(section => {
      animate(section, {
        opacity: [0, 1],
        translateY: [50, 0],
        duration: 1000,
        easing: 'easeOutExpo',
        autoplay: onScroll({
          target: section,
          threshold: 0.5 // el % del elemento visible para disparar animación
        })
      });
    });
  }
};
</script>

<style scoped>
.scroll-container {
  height: 600px;
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

.scroll-content {
  max-width: 600px; 
  display: flex;
  flex-direction: column;
  gap: 30px;
  padding: 20px;
  background-color: #1e1e1e;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.5);
}

.scroll-section {
  opacity: 0; 
  transform: translateY(50px); 
  transition: opacity 0.3s ease, transform 0.3s ease;
  padding: 15px;
  background-color: #2c2c2c;
  border-radius: 5px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.3);
}

.date {
  font-size: 1.2rem;
  font-weight: bold;
  color: #38e6ec;
  margin-bottom: 10px;
}

.description {
  font-size: 0.9rem;
  color: #ffffff;
}
</style>
