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
      <p class="frase">
        Web Developer
      </p>
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
      ease: 'inOutCirc', // global fallback
      loop: true,
      loopDelay: 1000
    });
  }
};
</script>

<style scoped>
.hero {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(135deg, #161616, #161616);
  text-align: center;
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

/* Media query para pantallas grandes */
@media (min-width: 1300px) {
  .animated-name {
    font-size: 155px;
    /* Tamaño más grande para pantallas de ordenador */
  }
}
.frase{
  color: white;
}
section {
  display: flex;
  flex-direction: column;
}
</style>
