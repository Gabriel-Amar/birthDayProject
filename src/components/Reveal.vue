<template>
  <div class="reveal">
    <div class="marquee-container gift-box">
      <!-- NES.css Button -->
      <button @click="openGift" class="nes-btn is-primary">{{ text }}</button>
    </div>
    <transition name="fade">
      <div v-if="isRevealed" class="reveal-message">
        <h1>Pack your bags – you’re off to Berlin for a Baby Metal concert!</h1>
      </div>
    </transition>
  </div>
</template>

<script>
import { gsap } from 'gsap';
import { confetti } from "@tsparticles/confetti";

export default {
  data() {
    return { isRevealed: false };
  },
  props: {
    text: {
      type: String,
      default: 'Redeem Gift'
    }
  },
  methods: {
    launchConfetti() {
      const end = Date.now() + 15 * 500;
      const colors = ["#bb0000", "#ffffff"];

      (function frame() {
        confetti({
          particleCount: 2,
          angle: 60,
          spread: 55,
          origin: { x: 0 },
          colors: colors,
        });

        confetti({
          particleCount: 2,
          angle: 120,
          spread: 55,
          origin: { x: 1 },
          colors: colors,
        });

        if (Date.now() < end) {
          requestAnimationFrame(frame);
        }
      })();

      confetti({
        spread: 360,
        ticks: 200,
        gravity: 1,
        decay: 0.94,
        startVelocity: 30,
        particleCount: 50,
        scalar: 3,
        shapes: ["image"],
        shapeOptions: {
          image: [{
            src: "https://banner2.cleanpng.com/20180702/pcg/aax18y8pm.webp",
            width: 32,
            height: 32,
          }],
        },
      });
    },
    openGift() {
      this.isRevealed = true;
      gsap.to('.gift-box', {
        duration: 1,
        scale: 0,
        onComplete: () => {
          this.launchConfetti();
          console.log('Confetti burst!');
        },
      });
    },
  },
};
</script>

<style scoped>
.reveal-message {
  text-align: center;
  padding: 20px;
  color: #fff;
  background: rgba(0, 0, 0, 0.7);
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}

.marquee-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

/* Centering the NES.css Button */
button.nes-btn {
  font-size: 1.5rem;
  padding: 10px 20px;
}
</style>
