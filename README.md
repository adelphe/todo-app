# Todo App

A lightweight, single-page Todo application built with **Vue 3** and **Vite**.

![Vue.js](https://img.shields.io/badge/Vue.js-3.4-4FC08D?logo=vuedotjs&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-5.0-646CFF?logo=vite&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-blue)

## Features

- Add new todos
- Mark todos as complete/incomplete
- Delete todos
- Live todo count display
- Clean, responsive UI

## Tech Stack

- **Vue 3** — Composition API with `<script setup>`
- **Vite** — Fast development server and optimized builds
- **Scoped CSS** — Component-level styling with no external UI libraries

## Project Structure

```
todo-app/
├── index.html
├── package.json
├── vite.config.js
└── src/
    ├── main.js          # App entry point
    ├── App.vue          # Root component & state management
    └── components/
        ├── TodoInput.vue   # Input form
        ├── TodoList.vue    # List container
        └── TodoItem.vue    # Individual todo item
```

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v16 or higher)
- npm

### Installation

```bash
git clone https://github.com/adelpheMusic/todo-app.git
cd todo-app
npm install
```

### Development

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

### Production Build

```bash
npm run build
npm run preview
```

## How It Works

The app follows a unidirectional data flow:

```
App.vue (state)
  ├── TodoInput.vue  →  emits "add-todo"  →  App.vue
  └── TodoList.vue
        └── TodoItem.vue  →  emits "toggle-complete" / "delete-todo"  →  App.vue
```

All state lives in `App.vue` using Vue's reactive `ref()`. Child components communicate upward through events.
