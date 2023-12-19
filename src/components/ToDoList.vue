<script setup lang="ts">
import { ref } from 'vue'
interface Task {
  name: string
  done: boolean
}

const tasks = ref<Task[]>([
  { name: '課題を殺す', done: false },
  { name: '絵を描く', done: false },
  { name: 'そうじ', done: false }
])

const newTaskName = ref('')

const addTask = () => {
  if (newTaskName.value == '') return
  tasks.value.push({
    name: newTaskName.value,
    done: false
  })
  newTaskName.value = ''
}
</script>

<template>
  <div>
    <div>ToDoList</div>
    <ul>
      <template v-for="task in tasks" :key="task.name">
        <div v-if="task.done == false">
          <label>{{ task.name }}<input type="checkbox" v-model="task.done" /></label>
        </div>
      </template>
    </ul>
    <div>完了!</div>
    <ul>
      <template v-for="task in tasks" :key="task.name">
        <div v-if="task.done == true">{{ task.name }}</div>
      </template>
    </ul>
    <div>
      <label>
        タスク
        <input v-model="newTaskName" placeholder="タスクを入力" type="text" />
      </label>
      <button @click="addTask">追加</button>
    </div>
  </div>
</template>

<style></style>
