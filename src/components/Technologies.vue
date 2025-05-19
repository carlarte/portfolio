<template>
  <div class="technologies-container">
    <div class="grid">
      <div class="tech-item" v-for="(tech, index) in technologies" :key="index">
        <img :src="tech.icon" :alt="tech.name" class="tech-icon" />
        <span class="tech-name">{{ tech.name }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      technologies: [
        {
          name: 'HTML5',
          icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg'
        },
        {
          name: 'CSS3',
          icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg'
        },
        {
          name: 'JavaScript',
          icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg'
        },
        {
          name: 'Vue.js',
          icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vuejs/vuejs-original.svg'
        },
        {
          name: 'PHP',
          icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg'
        },
        {
          name: 'Laravel',
          icon: 'https://upload.wikimedia.org/wikipedia/commons/9/9a/Laravel.svg'
        },
        {
          name: 'Python',
          icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg'
        },
        {
          name: 'Django',
          icon: 'https://static.djangoproject.com/img/logos/django-logo-negative.svg'
        },
        {
          name: 'JSON',
          icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/json/json-original.svg'
        },
        {
          name: 'Docker',
          icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original.svg'
        },
        {
          name: 'Ubuntu / GNU Linux',
          icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/ubuntu/ubuntu-plain.svg'
        },
        {
          name: 'OpenSUSE Tumbleweed',
          icon: 'https://upload.wikimedia.org/wikipedia/commons/thumb/d/d0/OpenSUSE_Logo.svg/1024px-OpenSUSE_Logo.svg.png'
        },
        {
          name: 'Bootstrap',
          icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/bootstrap/bootstrap-original.svg'
        },
        {
          name: 'GitHub',
          icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg'
        },
        {
          name: 'Figma',
          icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/figma/figma-original.svg'
        },
        {
          name: 'MySQL',
          icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mysql/mysql-original.svg'
        },
      ]
    };
  }
};
</script>

<style scoped>
.technologies-container {
  padding: 65px 50px;
  background-color: #1e1e1e;
  border-radius: 12px;
  max-width: 600px;
  margin: 0 auto;
}

.grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 30px;
  justify-items: center;
  align-items: center;
}

.tech-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  padding: 10px;
  border-radius: 10px;
  background-color: #2c2c2c;
  width: 100%;
}

.tech-item:hover {
  transform: scale(1.05);
}

.tech-icon {
  width: 60px;
  height: 60px;
  object-fit: contain;
  margin-bottom: 10px;
}

.tech-name {
  color: white;
  font-size: 14px;
  text-align: center;
}

@media (max-width: 600px) {
  .technologies-container {
    padding: 30px 5px;
    max-width: 100vw;
  }

  .grid {
    grid-template-columns: repeat(3, 1fr);
    gap: 15px;
  }

  .tech-item {
    padding: 5px;
  }

  .tech-icon {
    width: 40px;
    height: 40px;
  }
}
</style>
