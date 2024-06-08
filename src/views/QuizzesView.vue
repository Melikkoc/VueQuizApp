<script setup>
import q from '../data/quizzes.json';
import { ref, watch } from 'vue';
import Card from '../components/Card.vue';

const quizzes = ref(q);
const search = ref('');

watch(search, () => {
  quizzes.value = q.filter((quiz) =>
    quiz.name.toLowerCase().includes(search.value.toLowerCase())
  );
});
</script>

<template>
  <div class="container">
    <header>
      <h1 class="title">🌟 <span class="glow">Discover Quizzes</span> 🌟</h1>
      <input
        v-model.trim="search"
        type="text"
        placeholder="🔍 Search Quizzes..."
        class="search-input"
      />
    </header>
    <div class="options-container">
      <Card v-for="quiz in quizzes" :key="quiz.id" :quiz="quiz" />
    </div>
  </div>
</template>

<style scoped>
.container {
  max-width: 1000px;
  margin: 0 auto;
}

header {
  margin-bottom: 20px;
  margin-top: 40px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.title {
  font-weight: bold;
  font-size: 28px;
  color: #333;
}

.glow {
  animation: glowing 1.5s infinite;
  color: #ff8c00;
}

@keyframes glowing {
  0% {
    text-shadow: 0 0 10px #fff, 0 0 20px #ff8c00, 0 0 30px #ff8c00;
  }
  50% {
    text-shadow: 0 0 20px #fff, 0 0 30px #ff8c00, 0 0 40px #ff8c00;
  }
  100% {
    text-shadow: 0 0 10px #fff, 0 0 20px #ff8c00, 0 0 30px #ff8c00;
  }
}

.search-input {
  background-color: #f9f9f9;
  padding: 12px 15px;
  border-radius: 20px;
  border: 2px solid #ff6f61;
  font-size: 16px;
  transition: border-color 0.3s ease;
}

.search-input:focus {
  outline: none;
  border-color: #ff9f51;
}

.options-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
  margin-top: 40px;
  justify-content: center;
}
</style>
