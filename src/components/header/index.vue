<template>
    <header>
        <h1>{{ title }}</h1>
        <Button
            v-show="isHomePage" 
            :label="showAddTask ? 'Close' : 'Add Task'"
            :color="showAddTask ? 'red' : 'green'"
            @btn-click='$emit("toggle-add-task")'
        />
    </header>
</template>

<script>
import Button from "../button";

    export default {
        name: "Header",
        props: {
            title: String,
            showAddTask: Boolean
        },
        components: {
            Button,
        },
        computed :{
            isHomePage() {
                if(this.$route.path === '/'){
                    return true;
                } else {
                    return false;
                }
            }
        }
    }
</script>

<style scoped>
    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
    }
</style>