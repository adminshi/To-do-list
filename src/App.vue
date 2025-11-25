<script setup>
import { ref } from 'vue'
import Todolist from './components/todolist.vue'

const todos = ref([
  { id: 1, text: '学习', completed: false },
  { id: 2, text: '完成作业', completed: true },
  { id: 3, text: '锻炼身体', completed: false },
])

const handleUpdateCompleted = (id, newCompleted) => {
  const task = todos.value.find((item) => item.id === id)
  if (task) {
    task.completed = newCompleted
  }
}
</script>

<template>
  <div id="todo-list-app">
    <todolist :todolist="todos" @update:completed="handleUpdateCompleted"> </todolist>
  </div>
</template>

<style scoped></style>
