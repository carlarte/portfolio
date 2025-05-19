<template>
  <div class="scroll-container" ref="scrollContainer">
    <div class="scroll-content">
      <div
        v-for="(item, index) in reversedTimeline"
        :key="index"
        class="scroll-section"
        ref="sections"
      >
        <p class="date">{{ item.date }}</p>
        <h2 v-if="item.centro" class="centro">
          <a v-if="item.url" :href="item.url" class="centroLink" target="_blank" rel="noopener noreferrer">{{ item.centro }}</a>
          <span v-else>{{ item.centro }}</span>
        </h2>
        <h2 v-else class="empresa">
          <a v-if="item.url" :href="item.url" class="empresaLink" target="_blank" rel="noopener noreferrer">{{ item.empresa }}</a>
          <span v-else>{{ item.empresa }}</span>
        </h2>
        <h2 class="description">{{ item.description }}</h2>
        <br>
        <p class="skill">{{ item.skill }}</p>
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
        { date: "2010 - 2012", centro: "INS Salvador Seguí", description: "Técnica en Curas Auxiliares de Enfermería" },
        { date: "2013 - 2016", centro: "IES Eugeni d'Ors", description: "Técnica en Laboratorio de Diagnóstico Clínico" },
        { date: "2017 - 2022", empresa: "Hospital Municipal de Badalona (BSA)", url: "https://www.bsa.cat/", description: "5 años de experiencia como Auxiliar de Enfermería", skill: "Gestión eficaz del tiempo, asertividad, colaborar en equipo, gestión de las emociones, actitud proactiva" },
        { date: "2019 - 2021", centro: "Universitat de Barcelona (UB)", url: "https://www.ub.edu/portal/web/bellesarts", description: "(81 créditos) Grado de Bellas Artes" },
        { date: "Ene - Dic de 2023", centro: "Centre d'Estudis Politécnics (CEP)", url: "https://politecnics.barcelona/", description: "Actividades de gestión administrativa (SOC)" },
        { date: "2023 - 2025", centro: "Centre d'Estudis Politécnics (CEP)", url: "https://politecnics.barcelona/", description: "Técnica en Desarrollo de Aplicaciones Web", skill: "Gestión de proyectos desde cero"},
        { date: "Feb - Jun de 2025", empresa: "M-Automoción", url: "https://www.m-automocion.com/", description: "Prácticas como desarrolladora Web" , skill: "Configurar un servidor virgen, actualizar versiones de software, trabajar con entornos virtuales, creación de un whistleBlower y un acta de entrega con firma digital en móvil"}
      ]
    };
  },
  computed: {
    reversedTimeline() {
      return [...this.timeline].reverse();
    }
  },
  mounted() {
    this.$nextTick(() => {
      const sections = this.$refs.sections;
      const container = this.$refs.scrollContainer;

      // Asegurarse de que sections sea un array
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
.scroll-container {
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

.scroll-container::-webkit-scrollbar {
  display: none;
}

.scroll-content {
  max-width: 600px;
  display: flex;
  flex-direction: column;
  gap: 30px;
  padding: 20px;
  background-color: #1e1e1e;
  border-radius: 10px;
  
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
  font-size: 1rem;
  font-weight: bold;
  color: #ffffff;
  margin-bottom: 10px;
}

.centro {
  font-size: 1.5rem;
  font-weight: bold;
  color: #38e6ec;
  margin-bottom: 5px;
}

.empresa {
  font-size: 1.5rem;
  font-weight: bold;
  color: #FF5D5D;
  margin-bottom: 5px;
}

.description {
  font-size: 1rem;
  color: #ffffff;
}
.skill {
  font-style: italic;
  margin-top: 5px;
}
.centroLink {
  color: #38e6ec;
  text-decoration: none;
  transition: color 0.3s ease;
}
.empresaLink {
  color: #FF5D5D;
  text-decoration: none;
  transition: color 0.3s ease;
}
</style>
