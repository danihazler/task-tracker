<template>
    <AddTask 
      @add-task='addTask' 
      :showAddTask="showAddTask" 
    />
    <Tasks 
      :tasks="tasks" 
      @delete-task='deleteTask' 
    />
</template>

<script>
import Tasks from '../components/tasks';
import AddTask from '../components/add-task';

export default {
  name: 'Home',
  components: {
    Tasks,
    AddTask
  },
  props: {
    showAddTask: Boolean
  },
  data() {
    return { tasks: [] }
  },
  methods: {
    async deleteTask(id) {
      if(confirm('Are you sure?')){
        const res = await fetch(`api/tasks/${id}`, {
          method: 'DELETE',
        })

        res.status === 200
          ? (this.tasks = this.tasks.filter((task) => task.id !== id))
          : alert('Error deleting task')
      }
    },
    async addTask(task) {
      const res = await fetch('api/tasks', {
        method: 'POST',
        headers: {
          'Content-type': 'application/json'
        },
        body: JSON.stringify(task)
      })

      const data = await res.json();

      this.tasks = [...this.tasks, data];
    },
    async fetchTasks() {
      const res = await fetch('api/tasks');
      const data = await res.json();
      
      return data;
    },
  },
  async created() {
    this.tasks = await this.fetchTasks();
  },
}
</script>
