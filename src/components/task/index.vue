<template>
    <div :class="[task.reminder ? 'reminder' : '', 'task']">
       <h3>
           {{ task.text }}
           <i @click='$emit("delete-task", task.id)' class='fas fa-times'></i>
        </h3>
       <p>{{ task.day }}</p>
    </div>
</template>

<script>
    export default {
        name: 'Task',
        props: {
            task: Object,
        },
    }
</script>

<style scoped>
    .fas {
        color: red;
        transition: transform .3s;
    }
    .fas:hover {
        transform: scale(1.2);
        cursor: pointer;
    }
    .task {
        background: #f4f4f4;
        margin: 5px;
        padding: 10px 20px;
    }
    .task.reminder {
        border-left: 5px solid green;
    }
    .task h3 {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
</style>