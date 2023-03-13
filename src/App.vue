<script setup>
  import { RouterLink, RouterView } from 'vue-router'
  import q from "./data/quizes.json"
  import {ref, watch} from "vue"

  import Card from "./components/Card.vue"

  const quizes = ref(q)
  const search = ref("")

  watch(search, ()=>{
    console.log("hello, watch is called")
    quizes.value = q.filter( quiz => quiz.name.toLowerCase().includes(search.value.toLowerCase()))
  })
  
</script>

<template>
  <!-- <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView /> -->
  
  <div class="container max-w-5xl my-0 mx-auto">
    <header class="mb-2.5 mt-7 flex items-center">
      <h1 class="font-bold mr-7 ">Quizes</h1>
      <input v-model.trim="search" class="p-2.5 bg-slate-100 rounded-md" type="text" placeholder="Search...">
      {{ search }}
    </header>
    <div class="options-container flex flex-wrap mt-10">
      <!-- <div v-for="quiz in quizes" class="card w-80 overflow-hidden rounded-lg shadow-md mt-8 mr-5 cursor-pointer">
        <img class="w-full h-48 m-0" :src="quiz.img" alt="">
        <div class="cart-text py-0 px-1">
          <h2 class="font-bold">{{quiz.name}}</h2>
          <p class="">{{quiz.questions.length}} questions</p>
        </div>
      </div> -->
      <Card />
    </div>
  </div>
</template>

<style scoped>

</style>
