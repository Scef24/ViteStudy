<script setup>
import {ref} from 'vue'

const task = ref('')
const todos = ref([])

const addTask = ()=>{
  todos.value.push({description:task.value, done:false})
  task.value = ''
}
const Done = (index)=>{
        todos.value[index].done = !todos.value[index].done
  }
const deleteTask = (index)=>{
  todos.value.splice(index,1)
}
</script>

<template>
<header>
  <h1>To Do List</h1>
</header>
<div>
  <input type="text" v-model= "task" placeholder="Enter Task">
  <input type="submit" value="Enter" @click="addTask">

  <ul>
    <li v-for ="(todo,index) in todos" :key="index">
      <span :class = "{done: todo.done}">{{ todo.description}}</span>
    <button @click ="Done(index)" >Mark As Done</button>
    <button @click="deleteTask(index)">Delete</button>
    </li>
  </ul>
</div>
</template>

<style>

.done {
  color: red ;
}
</style>