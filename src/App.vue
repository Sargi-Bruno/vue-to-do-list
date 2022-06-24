<script setup>
import { ref } from 'vue'
import TaskCard from './components/TaskCard.vue'

const tasks = ref([])
const newTask = ref({
  title: '',
  description: ''
})

const createNewTask = () => {
  if(newTask.value.title === '') return

  tasks.value.push({
    title: newTask.value.title,
    description: newTask.value.description
  })

  newTask.value.title = ''
  newTask.value.description = ''
}

const handleRemove = (payload) => {
  tasks.value.splice(payload.index, 1)
}
</script>

<template>
  <div class="header">
    <h1>To Do List</h1>
  </div>
  <div class="content">
    <h2>Create a new task</h2>
    <div class="input-container">
      <input type="text" placeholder="Title" v-model="newTask.title">
      <input type="text" placeholder="Description" v-model="newTask.description">
      <button @click="createNewTask">Add</button>
    </div>
  </div>
  <div class="content">
    <div v-if="!tasks.length">
      <h2>You don't have any tasks yet</h2>
    </div>
    <div v-else>
      <div v-for="(task, index) in tasks" :key="index">
        <TaskCard
          :index="index"
          :title="task.title"
          :description="task.description"
          @remove="handleRemove"
        />
      </div>
    </div>
  </div>
</template>

<style>
body {
  background-color: #121212;
  color: #fff;
}
.header {
  display: flex;
  justify-content: center;
}
.header h1 {
  color: #fe6601;
}
.content {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.input-container {
  display: flex;
  flex-direction: column;
}
.input-container input {
  width: 20rem;
  height: 2rem;
  color: #fff;
  background-color: rgba(255, 255, 255, 0.08);
  border: none;
  border-radius: 4px;
  margin-bottom: 1rem;
}
.input-container button {
  width: 12rem;
  height: 3rem;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 4rem;
  background-color: #fe6601;
  color: #fff;
  font-size: 24px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
</style>
