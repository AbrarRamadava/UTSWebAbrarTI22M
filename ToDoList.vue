<script>
export default {
  name: 'ToDoList',
  data() {
    return {
      newTask: '',
      tasks: [
        { text: 'Tugas 1 Web', completed: false },
        { text: 'Tugas 3 Mobile', completed: false },
      ],
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim()) {
        this.tasks.push({ text: this.newTask, completed: false });
        this.newTask = '';
      }
    },
    toggleComplete(index) {
      this.tasks[index].completed = !this.tasks[index].completed;
    },
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
  },
};
</script>

<template>
    <div class="todo-list-container">
      <h1>Daftar Tugas</h1>
      <div class="input-container">
        <input
          v-model="newTask"
          @keyup.enter="addTask"
          type="text"
          placeholder="Masukkan tugas baru"
        />
        <button class="add-button" @click="addTask" :disabled="!newTask.trim()">Tambah</button>
      </div>
      <ul class="task-list">
        <li
          v-for="(task, index) in tasks"
          :key="index"
          :class="['task', { completed: task.completed }]"
          @click="toggleComplete(index)"
        >
          <span>{{ task.text }}</span>
          <button class="delete-btn" @click="deleteTask(index)">🗑️</button>
        </li>
      </ul>
    </div>
  </template>

  <style scoped>
  .todo-list-container {
    width: 100%;
    max-width: 800px;
    margin: 0 auto;
    padding: 30px;
    background-color: #f4f7fa;
    border-radius: 10px;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    text-align: center;
    font-family: 'Arial', sans-serif;
    margin-top: 30px;
  }
  h1 {
    font-size: 2.5em;
    color: #333;
    margin-bottom: 20px;
    font-weight: 600;
  }
  .input-container {
    display: flex;
    justify-content: space-between;
    margin-bottom: 30px;
  }
  input {
    width: 70%;
    padding: 15px;
    font-size: 14px;
    border: 2px solid #ddd;
    border-radius: 5px;
    outline: none;
    transition: border 0.3s ease;
  }
  input:focus {
    border-color: #4CAF50;
  }

  .add-button {
    width: 30%;
    padding: 15px;
    font-size: 14px;
    background-color: #4CAF50;
    color: white;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  .add-button:disabled {
    background-color: #ccc;
  }
  .add-button:hover {
    background-color: #45a049;
  }
  .task-list {
    list-style-type: none;
    padding: 0;
    margin: 0;
    max-height: 500px;
    overflow-y: auto;
    width: 100%;
  }
  .task {
    background-color: #fff;
    margin: 15px 0;
    padding: 15px;
    font-size: 14px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    cursor: pointer;
    transition: transform 0.2s ease, background-color 0.3s ease;
    color: black;
  }
  .task:hover {
    transform: scale(1.02);
  }
  .task.completed {
    background-color: #e0e0e0;
    text-decoration: line-through;
    color: black;
    opacity: 0.6;
  }
  .delete-btn {
    background: none;
    border: none;
    color: #e74c3c;
    font-size: 18px;
    cursor: pointer;
    transition: color 0.3s ease;
  }
  .delete-btn:hover {
    color: #c0392b;
  }
  @media (max-width: 600px) {
    .todo-list-container {
      width: 100%;
      padding: 15px;
    }
    input {
      width: 70%;
    }
    .add-button {
      width: 40%;
      font-size: 14px;
    }
  }
  </style>
  