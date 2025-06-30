<script setup lang="ts">

// Props are read-only, ? means it's optional
const props = defineProps<{
    taskTitle?: string;
}>();

// Emit an event, in this case for deletion, and send a string with it, in this case the title
const emit = defineEmits<{
    (event: 'deleteTask', taskTitle: string) : void;
}>();

// Function triggered, uses emit to send the event of deletion to parent
function deleteSelectedTask() {
    if(props.taskTitle) {
        emit('deleteTask', props.taskTitle);
    }
}

</script>

<template>

    <div class="tasksDiv col-md-4">
        <div class="card mb-3" >
            <div class="card-body">
                <h5 class="card-title">{{ taskTitle }}</h5>
                <h6 class="card-subtitle mt-2 text-muted">Description</h6>
                <input class="form-check-input" type="checkbox">
                <button class="btn btn-outline-danger" @click="deleteSelectedTask"><i class="bi bi-x"></i></button>
            </div>
        </div>
    </div>

</template>

<style scoped>

</style>