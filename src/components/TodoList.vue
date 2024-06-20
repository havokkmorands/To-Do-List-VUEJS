<script setup>
import { ref } from 'vue';

const newTask = ref('');
const tasks = ref([]);

function addTask() {
  if (newTask.value.trim()) {
    tasks.value.push(newTask.value.trim());
    newTask.value = '';
  }
}

function removeTask(index) {
  tasks.value.splice(index, 1);
}
</script>

<template>
    <div class="todo-list">
      <h1>Lista de Tarefas</h1>
      <input v-model="newTask" @keyup.enter="addTask" placeholder="Adicionar nova tarefa" />
      <button @click="addTask">Adicionar</button>
      <ul>
        <li v-for="(task, index) in tasks" :key="index">
          {{ task }}
          <button @click="removeTask(index)">Remover</button>
        </li>
      </ul>
    </div>
  </template>
  
  <style scoped>
  .todo-list {
    max-width: 400px;
    margin: 0 auto;
    text-align: center;
  }
  input {
    width: calc(100% - 22px);
    padding: 10px;
    margin-bottom: 10px;
  }
  button {
    margin-left: 10px;
    padding: 10px;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: flex;
    justify-content: space-between;
    margin-bottom: 5px;
  }
  </style>
  