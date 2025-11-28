<script setup>
import { computed, ref } from 'vue'
import Todolist from './components/todolist.vue'
import TodoButton from './components/todoButton.vue'

const todos = ref([
  { id: 1, text: '学习', completed: false },
  { id: 2, text: '完成作业', completed: true },
  { id: 3, text: '锻炼身体', completed: false },
])

const filterType = ref('all')
const filteredTodos = computed(() => {
  if (filterType.value === 'all') {
    return todos.value
  } else if (filterType.value === 'completed') {
    return todos.value.filter((item) => item.completed)
  } else if (filterType.value === 'uncompleted') {
    return todos.value.filter((item) => !item.completed)
  }
})
</script>

<template>
  <div id="todo-list-app">
    <todolist :todolist="filteredTodos"> </todolist>
    <todoButton @filter-type="filterType = $event"></todoButton>
  </div>
</template>

<style scoped></style>
