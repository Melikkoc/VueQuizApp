<script setup>
import { defineProps, computed } from 'vue';
import { RouterLink } from 'vue-router';

// Define props
const props = defineProps({
  quizQuestionLength: {
    type: Number,
    required: true,
  },
  numberOfCorrectAnswers: {
    type: Number,
    required: true,
  },
});

// Compute if all answers are correct
const allCorrect = computed(
  () => props.numberOfCorrectAnswers === props.quizQuestionLength
);
</script>

<template>
  <div :class="['results', { allCorrect }]">
    <p>Your Results</p>
    <div class="result-numbers">
      <span class="correct">{{ props.numberOfCorrectAnswers }}</span>
      <span class="separator">/</span>
      <span class="total">{{ props.quizQuestionLength }}</span>
    </div>
    <RouterLink to="/">
      <button>Go Back</button>
    </RouterLink>
  </div>
</template>

<style scoped>
.results {
  text-align: center;
  padding: 100px 0;
  font-weight: bold;
  background: linear-gradient(135deg, #f5f7fa, #c3cfe2);
  border-radius: 15px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
  margin: 50px auto;
  max-width: 600px;
  transition: background 0.3s ease;
}

.results.allCorrect {
  background: linear-gradient(135deg, #e0f7fa, #80cbc4);
}

.results p {
  font-size: 40px;
  margin-bottom: 20px;
  color: #333;
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.1);
}

.result-numbers {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 80px;
  font-weight: bold;
  margin-bottom: 30px;
  background: linear-gradient(45deg, #ff6f61, #de6262);
  border-radius: 10px;
  padding: 20px;
  color: #fff;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
  animation: bounce 1s infinite alternate;
}

.results.allCorrect .result-numbers {
  background: linear-gradient(45deg, #80ec86, #61d467);
}

.result-numbers .correct {
  color: #4caf50;
  background: linear-gradient(45deg, #66bb6a, #43a047);
  background-clip: text;
  animation: glow-green 1s infinite alternate;
}

.result-numbers .separator {
  margin: 0 15px;
  font-size: 60px;
  color: #fff;
}

.result-numbers .total {
  color: #f44336;
  background: linear-gradient(45deg, #ef5350, #e53935);
  background-clip: text;
  animation: glow-red 1s infinite alternate;
}

@keyframes glow-green {
  from {
    text-shadow: 0 0 10px rgba(76, 175, 80, 0.5);
  }
  to {
    text-shadow: 0 0 20px rgba(76, 175, 80, 1);
  }
}

@keyframes glow-red {
  from {
    text-shadow: 0 0 10px rgba(239, 83, 80, 0.5);
  }
  to {
    text-shadow: 0 0 20px rgba(239, 83, 80, 1);
  }
}

@keyframes bounce {
  from {
    transform: translateY(0);
  }
  to {
    transform: translateY(-10px);
  }
}

.results button {
  background-color: hsl(232, 100%, 80%);
  color: #fff;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 20px;
  font-weight: bold;
  transition: background-color 0.3s ease, transform 0.3s ease;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
}

.results button:hover {
  background-color: hsl(232, 100%, 70%);
  transform: scale(1.05);
}
</style>
