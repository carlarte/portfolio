<template>
    <div class="menu-container">
        <!-- Botones -->
        <div v-if="!showContent" class="menu-buttons">
            <button @click="selectView('CV')">Experiencia</button>
            <button @click="selectView('Technologies')">Tecnologías</button>
            <button @click="selectView('Projects')">Proyectos</button>
        </div>

        <!-- Contenido dinámico -->
        <div v-else class="menu-content">
            <component :is="currentComponent" />
        </div>
    </div>
</template>

<script>
import CV from './CV.vue';
import Technologies from './Technologies.vue';
import Projects from './Projects.vue';

export default {
    data() {
        return {
            currentView: null,
            showContent: false,
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
        },
    },
};
</script>

<style scoped>
.menu-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
  color: #ffffff;
}

.menu-buttons {
  display: flex;
  flex-direction: column;
  gap: 80px; 
  margin-bottom: 20px;
}

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
  transition: background-color 0.3s ease, box-shadow 0.3s ease;
  box-shadow: 0 0 15px #38e6ec, 0 0 25px #38e6ec, 0 0 35px #38e6ec; 
}

.menu-buttons button:hover {
  box-shadow: 0 0 15px #FF5D5D, 0 0 30px #FF5D5D, 0 0 45px #FF5D5D;
  /* font-weight: bold; */
}
.menu-buttons button:active {
  box-shadow: 0 0 15px #ffffff, 0 0 50px #FF5D5D, 0 0 70px #FF5D5D;
  /* font-weight: bold; */
}

.menu-content {
  text-align: center;
  width: 100%;
}
</style>