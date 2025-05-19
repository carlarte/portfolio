<template>
  <div class="menu-container">
    <!-- Botones siempre visibles y fijos -->
    <div :class="['menu-buttons', { 'mini': showContent }]">
      <button @click="selectView('CV')">Experiencia</button>
      <button @click="selectView('Technologies')">Tecnologías</button>
      <button @click="selectView('Projects')">Proyectos</button>
    </div>

    <!-- Contenido dinámico -->
    <component :is="currentComponent" @update-background="handleUpdateBackground" />
  </div>
</template>

<script>
import CV from './CV.vue';
import Technologies from './Technologies.vue';
import Projects from './Projects.vue';

import carla from '@/assets/projects/carla.png';
import code from '@/assets/projects/code.jpg';
import cohete from '@/assets/projects/cohete.png';

export default {
  data() {
    return {
      currentView: null,
      showContent: false,
      selectionImages: {
        CV: carla,
        Technologies: code,
        Projects: cohete,
      }
    };
  },
  computed: {
    currentComponent() {
      return {
        CV,
        Technologies,
        Projects,
      }[this.currentView];
    },
  },
  methods: {
    selectView(view) {
      this.currentView = view;
      this.showContent = true;
      this.$emit('update-background', this.selectionImages[view]);
    },
    handleUpdateBackground(image) {
    this.$emit('update-background', image);
    }
  },
};
</script>

<style scoped>
.menu-container {
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  padding: 20px;
  color: #ffffff;
  gap: 20px;
  position: relative;
}

/* Botones base */
.menu-buttons {
  display: flex;
  flex-direction: column;
  gap: 40px;
  position: sticky;
  top: 20px;
  left: 0;
  min-width: 160px;
  z-index: 10;
}

/* Tamaño normal */
.menu-buttons button {
  width: 150px;
  height: 150px;
  background-color: #161616;
  border: none;
  font-family: Poppins, sans-serif;
  border-radius: 50%;
  color: #ffffff;
  font-size: 16px;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 0 15px #38e6ec, 0 0 25px #38e6ec, 0 0 35px #38e6ec;
}

/* Tamaño reducido cuando hay contenido */
.menu-buttons.mini button {
  width: 85px;
  height: 85px;
  font-size: 12px;
  box-shadow: 0 0 20px #38e6ec;
}

/* Hover/Active */
.menu-buttons button:hover {
  box-shadow: 0 0 15px #FF5D5D, 0 0 30px #FF5D5D, 0 0 45px #FF5D5D;
}

.menu-buttons button:active {
  box-shadow: 0 0 15px #ffffff, 0 0 50px #FF5D5D, 0 0 70px #FF5D5D;
}

.menu-content {
  flex: 1;
}
@media (max-width: 600px) {
  .menu-container {
    flex-direction: column;
    align-items: stretch;
    padding: 10px;
    gap: 10px;
  }
  .menu-buttons {
    flex-direction: row;
    gap: 10px;
    position: static;
    min-width: unset;
    justify-content: center;
    width: 100%;
    margin-bottom: 10px;
  }
  .menu-buttons button,
  .menu-buttons.mini button {
    width: 60px;
    height: 60px;
    font-size: 10px;
    min-width: 0;
    min-height: 0;
    padding: 0;
  }
  .menu-content {
    width: 100%;
    overflow-x: auto;
    overflow-y: auto;
    max-width: 100vw;
    box-sizing: border-box;
  }
}
</style>
