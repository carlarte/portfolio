<template>
  <div class="scroll-container">
    <div class="scroll-content">
      <div
        v-for="(item, index) in timeline" :key="index" class="scroll-section" ref="sections">
        <p class="date">{{ item.date }}</p>
        <h2 class="centro">{{ item.centro }}</h2>
        <h2 class="empresa">{{ item.empresa }}</h2>
        <h2 class="description">{{ item.description }}</h2>
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
        { date: "2013 - 2016", centro: "IES Eugeni d'Ors",description: "Técnica en Labratorio de Diagnóstico Clínico" },
        { date: "2017 - 2022", empresa: "Hospital Municipal de Badalona (BSA)", description: "5 años de experiencia como Auxiliar de Enfermería" },
        { date: "2019 - 2021", centro: "Universitat de Barcelona (UB)", description: "(81 créditos) Grado de Bellas Artes" },
        { date: "Ene - Dic de 2023", centro: "Centre d'Estudis Politécnics", description: "Actividades de gestión administrativa (SOC)" },
        { date: "2023 - 2025", centro: "Centre d'Estudis Politécnics de Barcelona (CEP)", description: "Técnica en Desarrollo de Aplicaciones Web" },
        { date: "Feb - Jun de 2025", empresa: "M-Automoción", description: "Prácticas como desarrolladora Web" }
      ]
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
          threshold: 0.5
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
  font-size: 1rem;
  font-weight: bold;
  color: #ffffff;
  margin-bottom: 10px;
}
.centro{
  font-size: 1.5rem;
  font-weight: bold;
  color: #38e6ec;
  margin-bottom: 5px;
}
.empresa{
  font-size: 1.5rem;
  font-weight: bold;
  color: #FF5D5D;
  margin-bottom: 5px;
}

.description {
  font-size: 1rem;
  color: #ffffff;
}
</style>
