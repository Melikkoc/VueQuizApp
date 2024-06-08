<script setup>
import { defineProps } from 'vue';

const { questionStatus, barPercentage } = defineProps([
  'questionStatus',
  'barPercentage',
]);
</script>

<template>
  <header>
    <h1 class="question-title">Question: {{ questionStatus }}</h1>
    <div class="progress-container">
      <div class="progress-bar" :style="{ width: barPercentage }"></div>
    </div>
  </header>
</template>

<style scoped>
header {
  margin-top: 20px;
  text-align: center;
}

.question-title {
  font-size: 32px;
  color: #2c3e50;
  margin-bottom: 20px;
}

.progress-container {
  width: 80%;
  height: 20px;
  background-color: #ecf0f1;
  border-radius: 10px;
  margin: 0 auto;
  overflow: hidden;
}

.progress-bar {
  height: 100%;
  background-color: mediumseagreen;
  border-radius: 10px;
  transition: width 0.5s ease;
}
</style>
