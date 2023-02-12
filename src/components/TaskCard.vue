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
                @click="checkTask($event)"
                class="ma-0 pt-0 px-2"
                hide-details>
              </v-checkbox>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title>
              <div class="d-flex">
                <div class="col-11 pa-0">{{taskTitle}}</div>
                <div class="col-1">
                  <font-awesome-icon icon="fa-solid fa-pen-to-square" class="px-4" color="#0097A7" />
                  <font-awesome-icon icon="fa-solid fa-trash"  color="#0097A7" />
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
    },
    data: () => ({
      
    }),
    methods: {
      checkTask(event) {
        this.task.done = !this.task.done;
      }
    }
  }
</script>
