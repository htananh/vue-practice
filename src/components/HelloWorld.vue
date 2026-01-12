<script setup lang="ts">
import { ref } from 'vue'

defineProps<{ msg: string }>()

const count = ref(100)
const newTask = ref('')
const tasks = ref<string[]>([])

const addTask = () => {
  if (newTask.value.trim() !== '') {
    tasks.value.push(newTask.value.trim())
    newTask.value = ''
  }
}
const removeTask = (index: number) => {
  tasks.value.splice(index, 1)
}

</script>

<template>
  

  <div class="card">
    <button type="button" @click="count++">count IS {{ count }}</button>

  </div>
  <div class="card">
    <h2>To-Do List</h2>
    <input v-model="newTask" placeholder="Add a new task" @keyup.enter="addTask" />

    <button @click="addTask">Add Task</button>
    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        {{ task }}
        <button @click="removeTask(index)">Remove</button>
      </li>
    </ul>
  </div>
  
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
