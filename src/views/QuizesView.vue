<script setup>
  import { RouterLink, RouterView } from 'vue-router'
  import q from "../data/quizes.json"
  import {ref, watch} from "vue"

  import Card from "../components/Card.vue"

  const quizes = ref(q)
  const search = ref("")

  watch(search, ()=>{
    console.log("hello, watch is called")
    quizes.value = q.filter( quiz => quiz.name.toLowerCase().includes(search.value.toLowerCase()))
  })
  
</script>

<template>
    <header class="mb-2.5 mt-7 flex items-center">
      <h1 class="font-bold mr-7 ">Quizes</h1>
      <input v-model.trim="search" class="p-2.5 bg-slate-100 rounded-md" type="text" placeholder="Search...">
      {{ search }}
    </header>
    <div class="options-container flex flex-wrap mt-10">
      <Card v-for="quiz in quizes" :quiz="quiz  "/>
    </div>
</template>

<style scoped>

</style>
