<template>
  <ul class="list-group">
    <li
      class="list-group-item d-flex justify-content-between align-items-center"
      v-for="item in todolist"
      :key="item.id"
    >
      <!-- 复选框:点击更新状态 -->
      <div class="form-check">
        <input class="form-check-input" type="checkbox" :id="item.id" v-model="item.completed" />
        <label
          class="form-check-label"
          :for="item.id"
          :class="{ 'text-decoration-line-through': item.completed }"
        >
          {{ item.text }}
        </label>
      </div>

      <div class="task-actions">
        <span class="badge bg-success badge-pill" v-if="item.completed"> 已完成 </span>
        <span class="badge bg-warning badge-pill" v-else> 未完成 </span>
        <button class="delete-btn" @click="handleDelete(item.id)">删除</button>
      </div>
    </li>
  </ul>
</template>

<script setup>
const props = defineProps({
  todolist: {
    type: Array,
    required: true,
  },
})
const emit = defineEmits(['delete-task'])
const handleDelete = (id) => {
  emit('delete-task', id)
}
</script>

<style scoped>
.list-group {
  width: 500px;
  margin: 0 auto;
}
.text-decoration-line-through {
  color: #737a80;
}
.task-actions {
  display: flex;
  align-items: center;
}
.delete-btn {
  background-color: #ab3a3c;
  color: white;
  border: none;
  font-size: 0.7rem;
  padding: 2px 5px;
  border-radius: 5px;
}
.delete-btn:hover {
  background-color: #8f1e2a;
}
</style>
