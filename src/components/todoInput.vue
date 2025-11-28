<template>
  <div class="input-group mb-3">
    <div class="input-group-prepend">
      <span class="input-group-text" id="basic-addon1">新任务</span>
    </div>
    <input
      type="text"
      class="form-control"
      placeholder="请输入待办事项"
      aria-label="Username"
      aria-describedby="basic-addon1"
      v-model="newTask"
      @keyup.enter="onSubmit"
    />
    <button class="btn-primary" @click="onSubmit">添加</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const emit = defineEmits(['add-task'])

const newTask = ref('')

const tasks = ref([])

const onSubmit = () => {
  const task = newTask.value.trim()
  if (task) {
    const newTaskItem = {
      id: Date.now(),
      text: task,
      completed: false,
    }
    emit('add-task', newTaskItem)
    newTask.value = ''
  } else {
    alert('任务不能为空！请输入有效内容~')
  }
}
</script>

<style scoped>
.input-group {
  width: 500px;
  margin: 0 auto;
}
.btn-primary {
  background-color: #007bff;
  color: white;
  border: none;
}
</style>
