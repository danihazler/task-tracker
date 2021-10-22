<template>
    <form @submit="onSubmit" class="add-form" v-show="showAddTask" >
        <div class="form-control">
            <label for='task-text'>Task</label>
            <input type="text" v-model="text" name="text" placeholder="Add Task" id='task-text' />
        </div>
        <div class="form-control">
            <label for='date'>Day & Time</label>
            <input
                type="text"
                v-model="day"
                name="day"
                placeholder="Add Day & Time"
                id='date'
            />
        </div>
        <div class="form-control form-control-check">
            <label for='reminder'>Set Reminder</label>
            <input type="checkbox" v-model="reminder" name="reminder" id='reminder'/>
        </div>
        <input type="submit" value="Save Task" class="btn btn-block" />
    </form>
</template>

<script>
    export default {
        name: 'AddTask',
        props: {
            showAddTask: Boolean
        },
        data() {
            return {
                text: '',
                day: '',
                reminder: false
            }
        },
        methods: {
            onSubmit(evt) {
                evt.preventDefault();

                if(!this.text) {
                    alert('Please add a task');
                    return;
                }

                const newTask = {
                    // not necessary anymore, json-server creates an id
                    // id: Math.floor(Math.random() * 100000), 
                    text: this.text,
                    day: this.day,
                    reminder: this.reminder
                }

                this.$emit('add-task', newTask);

                this.text = '';
                this.day = '';
                this.reminder= false;
            }
        }
    }
</script>

<style scoped>
    .add-form {
        margin-bottom: 40px;
    }

    .form-control {
        margin: 20px 0;
    }

    .form-control label {
        display: block;
    }

    .form-control input {
        width: 100%;
        height: 40px;
        margin: 5px;
        padding: 3px 7px;
        font-size: 17px;
    }

    .form-control-check {
        display: flex;
        align-items: center;
        justify-content: flex-start;
    }

    .form-control-check input {
        height: 20px;
        width: 20%;
    }
</style>
