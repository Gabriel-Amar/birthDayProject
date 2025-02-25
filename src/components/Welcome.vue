<template>
   <div class="welcome">
    <div class="nes-container with-title is-centered is-dark">
      <p class="title">Happy Birthday!</p>
      <p>{{ name }} a special surprise awaits you...</p>
    </div>
    <div class="button-container">
      <button type="button" class="nes-btn is-primary" @click="$emit('next')">Begin</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ['name'],
};
</script>
<style>
.welcome {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

.button-container {
  display: flex;
  justify-content: center;
  width: 100%;
  margin-top: 20px;
}
</style>