<template>
  <section class="hero">
    <div>
      <h2 class="animated-name">
        <span v-for="(char, index) in nameArray" :key="index" class="letter">
          {{ char === ' ' ? '\u00A0' : char }}
        </span>
      </h2>
    </div>
    <div>
      <h2 class="frase">
        Escribo código, creo experiencias.
      </h2>
      <p class="frase1">
        Web Developer
      </p>
    </div>
    <div class="social-icons">
      <a href="https://github.com/carlarte" target="_blank" rel="noopener noreferrer">
        <img src="@/assets/Hero/github.png" alt="GitHub" />
      </a>
      <a href="https://linkedin.com/in/carlacayerohernandez" target="_blank" rel="noopener noreferrer">
        <img src="@/assets/Hero/linkedin.png" alt="LinkedIn" />
      </a>
      <a href="mailto:ccaarlaa@gmail.com" target="_blank" rel="noopener noreferrer">
        <img src="@/assets/Hero/gmail.png" alt="Gmail" />
      </a>
    </div>
    <div class="scroll" @click="scrollToAbout" style="cursor:pointer;">
      <img src="@/assets/flecha.png" alt="" srcset="">
    </div>
  </section>
  

</template>

<script>
import { animate } from 'animejs';

export default {
  name: 'Hero',
  data() {
    return {
      name: 'CARLA CAYERO'
    };
  },
  computed: {
    nameArray() {
      return this.name.split('');
    }
  },
  mounted() {
    animate('.letter', {
      y: [
        { to: '-2.75rem', ease: 'outExpo', duration: 600 },
        { to: 0, ease: 'outBounce', duration: 800, delay: 100 }
      ],
      rotate: {
        from: '-1turn',
        delay: 0
      },
      delay: (_, i) => i * 50,
      ease: 'inOutCirc',
      loop: true,
      loopDelay: 1000
    });
  },
  methods: {
  scrollToAbout() {
    const about = document.getElementById('about');
    if (about) {
      about.scrollIntoView({ behavior: 'smooth' });
    }
  }
}
};
</script>

<style scoped>
.hero {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #161616;
  text-align: center;
}
.scroll {
  position: absolute;
  left: 50%;
  bottom: 0;
  transform: translateX(-50%);
  margin-bottom: 20px;
}

.scroll img {
  width: 32px;
  height: auto;
  animation: neon-bounce 2.5s infinite;
  filter:
    drop-shadow(0 0 0px #fff)
    drop-shadow(0 0 8px #38fff9)
    drop-shadow(0 0 24px #38fff9)
    drop-shadow(0 0 48px #38fff9);
  transition: transform 0.3s ease, filter 0.3s;
}

@keyframes neon-bounce {
  0%, 100% {
    transform: translateY(0) scale(1);
    filter:
      drop-shadow(0 0 0px #fff)
      drop-shadow(0 0 8px #38fff9)
      drop-shadow(0 0 24px #38fff9)
      drop-shadow(0 0 48px #38fff9);
  }
  30% {
    transform: translateY(-16px) scale(1.15);
    filter:
      drop-shadow(0 0 8px #fff)
      drop-shadow(0 0 24px #38fff9)
      drop-shadow(0 0 48px #38fff9)
      drop-shadow(0 0 64px #38fff9);
  }
  60% {
    transform: translateY(0) scale(1);
    filter:
      drop-shadow(0 0 0px #fff)
      drop-shadow(0 0 8px #38fff9)
      drop-shadow(0 0 24px #38fff9)
      drop-shadow(0 0 48px #38fff9);
  }
}

.animated-name {
  font-size: 3rem;
  font-weight: 700;
  color: #38e6ec;
  text-transform: uppercase;
}

.letter {
  display: inline-block;
  opacity: 1;
}

.frase{
  color: #ffffff;
}
.frase1{
  color: #FF5D5D;
  font-weight: bold;
}

section {
  display: flex;
  flex-direction: column;
}
.social-icons {
  display: flex;
  justify-content: center;
  gap: 35px;
}

.social-icons img {
  width: 50px; 
  height: 50px;
  object-fit: contain; 
  transition: transform 0.3s ease; 
}

.social-icons img:hover {
  transform: scale(1.6); 
}


@media (min-width: 1000px) {
  .animated-name {
    font-size: 155px;
  }
}
</style>
