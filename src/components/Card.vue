<script setup>
import { defineProps } from 'vue';
import { useRouter } from 'vue-router';

// Define props
const props = defineProps({
  quiz: {
    type: Object,
    required: true,
  },
});

const router = useRouter();

const navigateToQuiz = () => {
  router.push(`/quiz/${props.quiz.id}`);
};
</script>

<template>
  <div class="card" @click="navigateToQuiz">
    <img :src="quiz.img" alt="image" />
    <div class="card-text">
      <h2>{{ quiz.name }}</h2>
      <p>{{ quiz.questions.length }} questions</p>
    </div>
  </div>
</template>

<style scoped>
.card {
  border: 1px solid #ddd;
  width: 100%;
  max-width: 310px;
  overflow: hidden;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  margin-bottom: 35px;
  margin-right: 20px;
  cursor: pointer;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
}

.card img {
  width: 100%;
  height: 190px;
  object-fit: cover;
  border-bottom: 1px solid #ddd;
}

.card .card-text {
  padding: 15px;
  background-color: #fff;
}

.card .card-text h2 {
  font-weight: bold;
  font-size: 1.5em;
  margin-bottom: 10px;
  color: #333;
}

.card .card-text p {
  font-size: 1em;
  color: #666;
}
</style>
