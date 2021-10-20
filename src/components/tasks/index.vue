<template>
    <ul>
        <li :key="task.id" v-for="task in tasks" >
            <Task :task='task' />
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
        }
    }
</script>