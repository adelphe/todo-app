<script setup>
import { ref } from 'vue'

const emit = defineEmits(['add-todo'])

const newTodoText = ref('')

function handleSubmit() {
  const text = newTodoText.value.trim()
  if (!text) return
  emit('add-todo', text)
  newTodoText.value = ''
}
</script>

<template>
  <form class="todo-input" @submit.prevent="handleSubmit">
    <input
      v-model="newTodoText"
      type="text"
      placeholder="What needs to be done?"
    />
    <button type="submit">Add Todo</button>
  </form>
</template>

<style scoped>
.todo-input {
  display: flex;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
}

.todo-input input {
  flex: 1;
  padding: 0.6rem 1rem;
  border: 1px solid #ddd;
  border-radius: 6px;
  font-size: 1rem;
  outline: none;
  transition: border-color 0.2s;
}

.todo-input input:focus {
  border-color: #3498db;
}

.todo-input button {
  padding: 0.6rem 1.2rem;
  background-color: #3498db;
  color: white;
  border: none;
  border-radius: 6px;
  font-size: 1rem;
  cursor: pointer;
  transition: background-color 0.2s;
}

.todo-input button:hover {
  background-color: #2980b9;
}
</style>
