<template>
  <div class="btn-group" role="group" aria-label="Basic example">
    <button
      type="button"
      class="btn"
      :class="{
        'btn-primary': selectedType === 'all',
        'btn-secondary': selectedType !== 'all',
      }"
      @click="emitFilter('all')"
    >
      全部
    </button>
    <button
      type="button"
      class="btn"
      :class="{
        'btn-primary': selectedType === 'completed',
        'btn-secondary': selectedType !== 'completed',
      }"
      @click="emitFilter('completed')"
    >
      已完成
    </button>
    <button
      type="button"
      class="btn"
      :class="{
        'btn-primary': selectedType === 'uncompleted',
        'btn-secondary': selectedType !== 'uncompleted',
      }"
      @click="emitFilter('uncompleted')"
    >
      未完成
    </button>
  </div>
</template>

<script setup>
import { ref, defineEmits } from 'vue'

const emit = defineEmits(['filter-type'])

const selectedType = ref('all')

const emitFilter = (type) => {
  selectedType.value = type
  emit('filter-type', type)
}
</script>

<style scoped>
.btn-group {
  width: 500px;
  margin: 30px auto;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.btn-primary {
  background-color: #007bff;
}
.btn-secondary {
  background-color: #6c757d;
}
</style>
