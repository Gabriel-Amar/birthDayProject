<template>
   <div id="app" :style="{ filter: `blur(${blurLevel}px)` }">
    <div class="background-image"></div>
     <div class="progress">
    <span>Step {{ currentStep + 1 }} of 3</span>
  </div>
    <component :is="currentComponent" @next="nextStep" :name="name" />
  </div>
</template>

<script>
import Welcome from './components/Welcome.vue';
import Clue1 from './components/Clue1.vue';
import Reveal from './components/Reveal.vue';

export default {
  data() {
    return {
      currentStep: 0,
      blurLevel: 0, // Initial blur for background image
      components: [Welcome, Clue1, Reveal],
    };
  },
  computed: {
    currentComponent() {
      return this.components[this.currentStep];
    },
    name() {
      return 'Camilla';
    },
  },
  methods: {
    nextStep() {
      if (this.currentStep < this.components.length - 1) {
        this.currentStep++;
      }
    },
  },
};
</script>

<style>
.progress { text-align: center; padding: 10px; }
#app{
  background: grey;
}
</style>
