<script setup>
import { ref } from 'vue'
import Todolist from './components/todolist.vue'

const todos = ref([
  { id: 1, text: '学习', completed: false },
  { id: 2, text: '完成作业', completed: true },
  { id: 3, text: '锻炼身体', completed: false },
])
</script>

<template>
  <div id="todo-list-app">
    <todolist :todolist="todos"> </todolist>
  </div>
</template>

<style scoped></style>
