<script setup>
import { ref } from 'vue';

// const fullTasks =([

// ])

// const taskNams = ref("")
// const timeTasks = ref("")

// function taskAddedNew(){
//   const tsk = prompt('what is the task name?')
//   const tmtk = prompt('What is the task time')

//   taskNams.value = tsk
//   timeTasks.value = tmtk

//   fullTasks.value = taskNams
//   fullTasks.value = timeTasks
// }



const taskInfos = ref([

])

const task = ref("")

function addNewTask(){
  taskInfos.value.push(task.value)
  task.value = ""
}

</script>

<template>

<div class="flex mx-4 justify-between w-full">
<form @submit.prevent action="#">
  <input type="text" @keypress.enter="addNewTask()" v-model="task" name="man">
  <input type="number" name="numbr" @keypress.enter="addNewTask()">
  <button type="submit" @click="addNewTask()" class="bg-blue-500">Send</button>
</form>
</div>


<div class="flex justify-end mb-2" v-for="(taskInfo,index) in taskInfos" :key="index">
  <div class="rounded py-2 px-3 bg-green-500">
    <h4 class="text-md mt-1">{{ taskInfo }}</h4>
  </div>
</div>


<!-- <button @click="taskAddedNew()" >Click Here</button> -->

</template>

<style>

</style>