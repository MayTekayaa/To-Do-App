<template>
  <v-container>
    <v-row class="text-center">
      <v-col class="mb-4">
        <h4 class="display-2 font-weight-bold mb-3">
          Schedule your goal
        </h4>
      </v-col>
    </v-row>
    
    <v-row class="justify-end my-5 mx-16">
      <v-btn class="text-capitalize rounded-pill"  style="background: white; color: #0097A7;" @click="clickToAdd">
        <font-awesome-icon class="px-2" icon="fa-solid fa-plus" />
        <span class="hidden-md-and-down"> Add Task </span>
      </v-btn>
    </v-row>
   <TasksList/>
   <AddTaskDrawer :value="clickedDrawer" ref="taskDrawer" />
  </v-container>
</template>

<script>
import TasksList from './TasksList.vue';
import AddTaskDrawer from './AddTaskDrawer.vue';

export default {
    name: 'Home',

    components: {
      TasksList,
      AddTaskDrawer
    },

    data: () => ({
      clickedDrawer: true
    }),
    methods: {
      clickToAdd() {
        this.$refs.taskDrawer.open();
      },
    }
  }
</script>
