<template>
  <div class="progress">
    <span>Step {{ currentStep + 1 }} of 3</span>
  </div>
</template>

<script>
  name: "ProgressIndicator"
export default {
  props: ['currentStep'],
};
</script>

<style>
.progress { text-align: center; padding: 10px; }
</style>