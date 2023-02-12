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
      tasksList: [
        {
          id: 'task_01',
          title: 'To Do 1',
          done: false,
          description:'Desc1',
          deadline: new Date('December 17, 2022 03:24:00'),
        },
        {
          id:'task_02',
          title:'To Do 2',
          done: false,
          description:'Desc2',
          deadline: new Date('December 17, 2022 03:24:00'),
        },
        {
          id:'task_03',
          title:'To Do 3',
          done: true,
          description:'Desc3',
          deadline: new Date('December 17, 2022 03:24:00'),
        }
      ]
    }),
  }
</script>
