<script setup>
  import { useRouter } from 'vue-router';

  const router = useRouter()
  const {quiz} = defineProps(['quiz'])
  console.log(quiz)

  const navigateToQuiz = () => {
    router.push(`/quiz/${quiz.id}`)
  }
</script>

<template>
      <div @click="navigateToQuiz()" class="card w-80 overflow-hidden rounded-lg shadow-md mt-8 mr-5 cursor-pointer">
        <img class="w-full h-48 m-0" :src="quiz.img" alt="">
        <div class="cart-text py-0 px-1">
          <h2 class="font-bold">{{quiz.name}}</h2>
          <p class="">{{ quiz.questions.length }} questions</p>
        </div>
      </div>
</template>