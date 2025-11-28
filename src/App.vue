<script setup>
import { computed, ref } from 'vue'
import Todolist from './components/todolist.vue'
import TodoButton from './components/todoButton.vue'
import TodoInput from './components/todoInput.vue'
import ClearButton from './components/clearButton.vue'

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

const addNewTask = (newTask) => {
  todos.value.push(newTask)
}

const clearAllTasks = () => {
  todos.value = []
}
</script>

<template>
  <div id="todo-list-app">
    <div class="todo-header">
      <h3>本周待办事项列表</h3>
    </div>
    <todoInput @add-task="addNewTask"></todoInput>
    <todolist :todolist="filteredTodos"> </todolist>
    <todoButton @filter-type="filterType = $event"></todoButton>
    <clearButton :has-tasks="todos.length > 0" @clear-all="clearAllTasks"> </clearButton>
  </div>
</template>

<style scoped>
.todo-header {
  text-align: center;
  margin: 20px 0;
}
</style>
