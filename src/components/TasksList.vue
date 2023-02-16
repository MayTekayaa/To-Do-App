<template>
  <v-container>
    <div
      v-for="task in tasksList"
      :key="task.id"
      class="mx-14 py-3">
     <TaskCard :task="task"/>
    </div>
  </v-container>
</template>

<script>
import TaskCard from './TaskCard.vue';

export default {
  name: 'TasksList',

  components: {
    TaskCard,
  },

  data: () => ({
    tasksList: [],
    displayAlert: false,
  }),
  created() {
    document.addEventListener('add-task-event', event => {
      if (event && event.detail) {
        this.tasksList.push({id: this.tasksList.length, title: event.detail.taskTitle, description: event.detail.taskDescription, deadline: event.detail.taskDueDate, done: false});
      }
    });
    document.addEventListener('archive-task', event => {
      if (event && event.detail) {
        const tasks = this.tasksList.filter(task => task.id !== event.detail.id);
        this.tasksList = tasks;
      }
      this.displayAlert= true;
    });
    document.addEventListener('delete-task', event => {
      if (event && event.detail) {
        const tasks = this.tasksList.filter(task => task.id !== event.detail.id);
        this.tasksList = tasks;
      }
    });
  }
}
</script>
