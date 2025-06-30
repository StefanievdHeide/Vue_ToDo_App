<script setup lang="ts">

import tasksDiv from './components/TasksCreation.vue'

import { ref } from 'vue';

const tasksArray = ref<string[]>([]);
const userInput = ref('');

function addTask() {
    tasksArray.value.push(userInput.value);
    userInput.value = "";
}

</script>

<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-10 text-md-start mt-md-5">
                <h2>To do list</h2>
            </div>
        </div>

        <div class="row justify-content-center">
            <div class="col-md-5">
                <input type="text" v-model="userInput">
                <button @click="addTask()">Add Task</button>
            </div>
        </div>

        <div v-for="title in tasksArray" class="row">

            <tasksDiv :taskTitle="title"></tasksDiv>

        </div>
    </div>

</template>

<style scoped>


</style>