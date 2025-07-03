<script setup lang="ts">

import { ref } from 'vue'

const checkedTasks = ref(false)

// Props = input → child
// Emits = output → parent

// Props are read-only, ? means it's optional, recieve the title and id from parent

// props.counterInterface.taskTitle
const props = defineProps<{
    taskTitle?: string;
    taskID: number;
}>();

// Emit an event to the parent, in this case for deletion, and send a string with it, in this case the title
const emit = defineEmits<{
    (event: 'deleteTask', taskID: number) : void;
}>();

// Function triggered, uses emit to send the event of deletion to parent
function deleteSelectedTask() {
    if(props.taskID !== undefined) {
        emit('deleteTask', props.taskID);
    }
}

</script>

<template>

    <div class="tasksDiv">
        <div class="card">
            <div class="card-body">
                <div class="d-flex align-items-center justify-content-between gap-2">
                    <div class="d-flex align-items-center gap-2 flex-grow-1">
                        <input class="form-check-input" type="checkbox" :value="props.taskID" v-model="checkedTasks">
                        <h5 class="card-title mb-0" :class="{ 'text-decoration-line-through': checkedTasks }">
                            {{ taskTitle }}
                        </h5>
                    </div>

                <button class="btn btn-outline-danger btn-sm" @click="deleteSelectedTask">
                    <i class="bi bi-x"></i>
                </button>
                </div>
            </div>
        </div>
    </div>

</template>

<style scoped>

</style>