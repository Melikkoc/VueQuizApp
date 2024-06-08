<script setup>
import { defineProps, defineEmits } from 'vue';

const emit = defineEmits(['selectOption']);

const { question } = defineProps(['question']);

const emitSelectedOption = (isCorrect) => {
  emit('selectOption', isCorrect);
};
</script>

<template>
  <div class="question-container">
    <h1 class="question">{{ question.text }}</h1>
  </div>
  <div class="options-container">
    <div
      v-for="option in question.options"
      :key="option.id"
      class="option"
      @click="emitSelectedOption(option.isCorrect)"
    >
      <p class="option-label">{{ option.label }}</p>
      <div class="option-value">
        <p>{{ option.text }}</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.question-container {
  margin-top: 20px;
  text-align: center;
}

.question {
  font-size: 24px;
  margin-bottom: 20px;
}

.options-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.option {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
  width: 100%;
  max-width: 600px;
  cursor: pointer;
  border-radius: 10px;
  overflow: hidden;
  transition: background-color 0.3s, transform 0.3s;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
  animation: glow 1.5s infinite alternate;
}

.option:hover {
  background-color: #f2f2f2;
  transform: translateY(-2px);
}

.option-label {
  background-color: #ff6363;
  color: white;
  border-radius: 50%;
  width: 50px;
  height: 50px;
  font-size: 24px;
  margin-left: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-right: 15px;
}

.option-value {
  background-color: #94a3ff;
  border-radius: 10px;
  flex-grow: 1;
  height: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 20px;
  margin-right: 10px;
  padding: 0 20px;
  color: #fff;
}

@keyframes glow {
  from {
    box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
  }
  to {
    box-shadow: 0px 0px 15px #5269fa;
  }
}

.search-bar {
  background-color: #94a3ff;
  color: white;
}
</style>
