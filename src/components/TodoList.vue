<script setup>
import TodoItem from './TodoItem.vue'

defineProps({
  todos: {
    type: Array,
    required: true
  }
})

defineEmits(['toggle-complete', 'delete-todo'])
</script>

<template>
  <div class="todo-list">
    <TodoItem
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @toggle-complete="$emit('toggle-complete', $event)"
      @delete-todo="$emit('delete-todo', $event)"
    />
  </div>
</template>

<style scoped>
.todo-list {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}
</style>
