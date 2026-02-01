<script setup>
import { ref } from 'vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'

// Todo structure: { id: number, text: string, completed: boolean }

const todos = ref([
  { id: 1, text: 'Learn Vue.js', completed: false },
  { id: 2, text: 'Build Todo App', completed: false },
  { id: 3, text: 'Deploy to production', completed: false }
])

function addTodo(text) {
  todos.value.push({
    id: Date.now(),
    text,
    completed: false
  })
}

function deleteTodo(id) {
  todos.value = todos.value.filter(todo => todo.id !== id)
}

function updateTodo(id, newText) {
  const todo = todos.value.find(todo => todo.id === id)
  if (todo) {
    todo.text = newText
  }
}

function toggleComplete(id) {
  const todo = todos.value.find(todo => todo.id === id)
  if (todo) {
    todo.completed = !todo.completed
  }
}
</script>

<template>
  <div class="app">
    <h1>Todo App</h1>
    <TodoInput @add-todo="addTodo" />
    <TodoList
      :todos="todos"
      @toggle-complete="toggleComplete"
      @delete-todo="deleteTodo"
    />
    <p class="todo-count" v-if="todos.length === 0">No todos yet. Add one above!</p>
    <p class="todo-count" v-else>{{ todos.length }} todo{{ todos.length !== 1 ? 's' : '' }}</p>
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
    Ubuntu, Cantarell, sans-serif;
  background-color: #f5f5f5;
  color: #333;
}

.app {
  max-width: 600px;
  margin: 0 auto;
  padding: 2rem 1rem;
}

h1 {
  margin-bottom: 1.5rem;
  text-align: center;
  color: #2c3e50;
}

.todo-count {
  text-align: center;
  margin-top: 1rem;
  color: #888;
  font-size: 0.9rem;
}
</style>
