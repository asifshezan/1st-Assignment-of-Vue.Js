<script setup>
import { ref } from 'vue';

const tasks = ref([
  {
    name: 'task-1',
    time: '4:50px'
  },
  {
    name: 'task-2',
    time: '6:40am'
  }
])


const newTaskName = ref('')
const newTaskTime = ref('')


function addNewTask(){
  const newTask = {
    name: newTaskName.value,
    time: newTaskTime.value
  }

  console.log(newTask);

  newTaskName.value('');
  newTaskTime.value('');

}


function deleteTask(index){
  tasks.value.splice(index,1)
}


const popupForm = ref(false);

</script>

<template>

<div>
  <button @click="popupForm =! popupForm" type="button" class="bg-blue-500"> Fill up Form</button>
</div>

<form v-if="popupForm"  class="max-w-sm mx-auto" action="">
  <div class="mr-5 flex flex-row ">
    <div class="mr-5 text-center">
    <label  class="block mb-2 text-sm font-medium text-gray-900 ">Task Name</label>
    <input v-model="newTaskName" type="text" class="shadow-sm bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 " placeholder="Enter Task Name" >
    </div>
    <div class="text-center">
    <label  class="block mb-2 text-sm font-medium text-gray-900 ">Task Time</label>
    <input v-model="newTaskTime" type="number" class="shadow-sm bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 " placeholder="Enter Task Time" >
    </div>
    
  </div>
  <div class="text-center mt-5">
    <button @click="addNewTask()" type="submit" class="text-center text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2 ">Add Task</button>
  </div>
</form>


<div v-for="(task,index) in tasks" :key="index" class="w-96 mx-auto max-w-md p-4 mt-10 bg-yelllow text-black-700 border border-gray-200 rounded-lg shadow sm:p-8">
<ul>
  <li>
    <h3>{{ task.name }}</h3>
    <h3>{{ task.time }}</h3>

    <div>
      <button @click="deleteTask()" type="button" class="bg-red-500">Delete</button>
    </div>
  </li>
</ul>

</div>



</template>

<style>

</style>