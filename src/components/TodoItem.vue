<script setup>
defineProps({
  todo: {
    type: Object,
    required: true
  }
})

defineEmits(['toggle-complete', 'delete-todo'])
</script>

<template>
  <div class="todo-item">
    <label class="todo-content">
      <input
        type="checkbox"
        :checked="todo.completed"
        @change="$emit('toggle-complete', todo.id)"
      />
      <span :class="{ completed: todo.completed }">{{ todo.text }}</span>
    </label>
    <button class="delete-btn" @click="$emit('delete-todo', todo.id)">×</button>
  </div>
</template>

<style scoped>
.todo-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0.75rem 1rem;
  background-color: white;
  border: 1px solid #eee;
  border-radius: 6px;
}

.todo-content {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  cursor: pointer;
  flex: 1;
}

.todo-content input[type="checkbox"] {
  width: 18px;
  height: 18px;
  cursor: pointer;
}

.todo-content span {
  font-size: 1rem;
  transition: all 0.2s;
}

.todo-content span.completed {
  text-decoration: line-through;
  opacity: 0.5;
}

.delete-btn {
  background: none;
  border: none;
  color: #e74c3c;
  font-size: 1.4rem;
  cursor: pointer;
  padding: 0 0.25rem;
  line-height: 1;
  transition: color 0.2s;
}

.delete-btn:hover {
  color: #c0392b;
}
</style>
