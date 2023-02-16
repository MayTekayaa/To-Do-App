<template>
  <v-card 
    class="py-5"
    outlined
    hover>
    <v-list>
      <v-list-item>
        <v-list-item-icon class="ma-6">
          <v-checkbox
            color="success"
            class="ma-0 pt-0 px-2"
            hide-details
            @click="checkTask">
          </v-checkbox>
        </v-list-item-icon>
        <v-list-item-content>
          <v-list-item-title>
            <div class="d-flex">
              <div class="col-10 pa-0">{{taskTitle}}</div>
              <span class="col-1" :class="validDate && 'green--text' || ' red--text'">
                {{taskDeadline}}
              </span>
              <div class="col-1">
                <font-awesome-icon icon="fa-solid fa-pen-to-square" class="px-4" color="#0097A7" />
                <font-awesome-icon icon="fa-solid fa-trash"  color="#0097A7" @click="deleteTask" />
              </div>
            </div>
          </v-list-item-title>
          <v-list-item-subtitle>
            {{taskDescription}}
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </v-card>
</template>

<script>
export default {
  name: 'TaskCard',

  props: {
    task: {
      type: Object,
      default: null,
    },
  },
  computed: {
    taskTitle() {
      return this.task.title;
    },
    taskDescription() {
      return this.task.description;
    },
    taskStatus() {
      return this.task.done;
    },
    taskDeadline() {
      return this.task.deadline;
    },
    validDate() {
      const today = new Date();
      var taskDate = new Date(this.taskDeadline); 
      return taskDate >= today;
    }
  },
  methods: {
    checkTask() {
      document.dispatchEvent(new CustomEvent('archive-task',
        { detail: { id: this.task.id} }));
        //To be added in archieved tasks
    },
    deleteTask() {
      document.dispatchEvent(new CustomEvent('delete-task',
        { detail: { id: this.task.id} }));
    },
    
  }
}
</script>
