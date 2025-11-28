<template>
  <button type="button" class="clear-btn" @click="handleClear" :disabled="!hasTasks">
    清空所有
  </button>
</template>

<script setup>
const props = defineProps({
  hasTasks: {
    type: Boolean,
    required: true,
  },
})

const emit = defineEmits(['clear-all'])

const handleClear = () => {
  emit('clear-all')
}
</script>

<style scoped>
.clear-btn {
  background-color: #585a5e;
  color: white;
  margin: 0 auto;
  display: block;
  border: none;
  padding: 10px 15px;
  border-radius: 4px;
}
.clear-btn:hover {
  background-color: #303030;
}
</style>
