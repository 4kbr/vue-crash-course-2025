<script setup lang="ts">
import { onMounted, ref } from 'vue';
// options API
let staatus = ref("active")

const changeData = () => {
  if (staatus.value === "active") {
    staatus.value = 'pending'
  } else {
    staatus.value = 'active'
  }
}

const tasks = ref(['task on1', 'task on2'])
const newTask = ref('')

const addTask = () => {
  if (newTask.value?.trim() !== "") {
    tasks.value.push(newTask.value);
    newTask.value = '';
  }
}

const deleteTask = (index: number) => {
  tasks.value.splice(index, 1)
}

onMounted(async () => {
  try {
    const url = 'https://jsonplaceholder.typicode.com/todos'
    const response = await fetch(url);
    const data = await response.json() as { title: string }[];
    tasks.value = data.map(task => task.title);
  } catch (error) {
    console.log('error fetcing url');
  }
})

</script>

<template>
  <h1>{{ staatus }}</h1>
  <p v-if="staatus === 'active'">User is active</p>
  <p v-else-if="staatus === 'pending'">User is Pending</p>
  <p v-else>User is Inactive</p>
  <!-- <button :onclick="changeData">clikc</button> -->
  <!-- lebih best practice -->
  <button @click="changeData">clikc</button>

  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask" />
    <button type="submit">Submit</button>
  </form>

  <h3>Task:</h3>
  <ul>
    <li v-for="(task, index) in tasks" :key="index">
      <span>{{ task }}</span>
      <button @click="deleteTask(index)">x</button>
    </li>
  </ul>
</template>

<style>
h1 {
  color: aqua;
}
</style>