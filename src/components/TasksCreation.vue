<script setup lang="ts">
import { ref } from 'vue';

const task = ref('');

defineProps<{
    taskTitle?: string;
}>();

</script>

<template>

    <div class="tasksDiv">

        <p>{{ taskTitle }}</p>

    </div>


</template>

<style scoped>

.tasksDiv {
    background-color: blueviolet;
    margin-bottom: 35px;
}

</style>