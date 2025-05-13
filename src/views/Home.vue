<template>
  <div class="square"></div>
</template>

<script>
import { animate, stagger } from 'animejs';

export default {
  name: 'Home',
  mounted() {
    animate('.square', {
      x: 320,
      rotate: { from: -180 },
      duration: 1250,
      delay: stagger(65, { from: 'center' }),
      easing: 'easeInOutQuint',
      loop: true,
      direction: 'alternate'
    });
  }
}
</script>

<style>
.square {
  width: 100px;
  height: 100px;
  background-color: #007BFF;
}
</style>