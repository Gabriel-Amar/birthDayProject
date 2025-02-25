<template>
  <div class="clue">
    <div class="content-container">
      <h2>{{ name }}, Discover Your Destination</h2>
      <p>Which city is known for the Brandenburg Gate?</p>
      <div class="button-container">
        <button
          v-for="option in options"
          :key="option"
          class="nes-btn is-primary"
          @click="checkAnswer(option)"
        >
          {{ option }}
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['name'],
  data() {
    return {
      options: ['Paris', 'Berlin', 'London'],
    };
  },
  methods: {
    checkAnswer(answer) {
      if (answer === 'Berlin') {
        this.$emit('next');
      } else {
        alert('Not quite, try again!');
      }
    },
  },
};
</script>

<style scoped>
.clue {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

.content-container {
  text-align: center;
}

.button-container {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin-top: 20px;
}
</style>
