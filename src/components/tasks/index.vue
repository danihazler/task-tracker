<template>
    <ul>
        <li :key="task.id" v-for="task in tasks" >
            <Task :task='task' @delete-task='$emit("delete-task", task.id)' />
        </li>
   </ul>
</template>

<script>
import Task from '../task';

    export default { 
        name: 'Tasks',
        props: {
            tasks: Array,
        },
        components: {
            Task
        },
        emits: ['delete-task']
    }
</script>