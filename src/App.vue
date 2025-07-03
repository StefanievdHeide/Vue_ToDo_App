<script setup lang="ts">

import tasksDiv from './components/TaskCards.vue'
import { ref } from 'vue';
import type { Itasks } from './tasks';

let idTrack = 0;

const tasksArray = ref<Itasks[]>([]);
// add boolean done
const userInput = ref('');

function addTask() {
    tasksArray.value.push({
        id: idTrack++,
        title: userInput.value
    })
    userInput.value = "";
    console.log(tasksArray.value);
}

// Filters through the array using the given string to filter those out
function handleDeletion(taskID: number) {
    tasksArray.value = tasksArray.value.filter(task => task.id !== taskID);
}

</script>

<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col text-md-center mt-md-2 mb-3">
                <h2>To do list</h2>
            </div>
        </div>

        <div class="row justify-content-center">
            <div class="col-md-6">
                <div class="input-group mb-3">
                    <span class="input-group-text"><i class="bi bi-list-task"></i></span>  
                    <input class="form-control" type="text" v-model="userInput">
                    <button class="btn btn-outline-secondary" type="button" @click="addTask()">Add Task</button>
                </div>
            </div>
        </div>

        <div class="row d-flex justify-content-center">
            <div class="col-md-10 overflow-auto">
                <div class="d-flex flex-column align-items-center gap-3" style="height: 550px">
                    <div v-for="task in tasksArray" :key="task.id" class="w-100">
                        <!-- send out to 'taskDiv' string called taskTitle -->
                        <!-- @deleteTask, listens for event from child, then function called by parent -->
                        <tasksDiv :taskID="task.id" :taskTitle="task.title" @deleteTask="handleDeletion"></tasksDiv>
                    </div>
                </div>
            </div>
        </div>
            
    </div>

</template>

<style scoped>


</style>