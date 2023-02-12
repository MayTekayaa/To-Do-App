<template>
  <v-navigation-drawer
    v-model="drawer"
    right
    fixed
    absolute
    temporary
    height="100%"
    :width="smallScreen && '100%' || '25%'">
    <v-card height="100%" flat>
      <v-card-title>
        Create a Task 
        <v-spacer />
        <font-awesome-icon icon="fa-solid fa-xmark" @click="close" />
      </v-card-title>
      <v-divider class="py-4" />
      <div class="pa-2 mx-3">
        <v-text-field
          label="Enter the name of the task"
          :rules="rules"
          hide-details="auto" />
      </div>
      <div class="pa-2 mx-3">
        <v-textarea 
          label="Enter the description of the task"
          class="mt-y" />
      </div>
      <div class="pa-2 mx-3">
        <v-menu
          ref="menu"
          v-model="menu"
          :close-on-content-click="false"
          :return-value.sync="date"
          transition="scale-transition"
          offset-y
          max-width="290px"
          min-width="auto">
          <template v-slot:activator="{ on, attrs }">
            <v-text-field
              v-model="date"
              label="Pick a due date"
              prepend-icon="mdi-calendar"
              readonly
              v-bind="attrs"
              v-on="on">
            </v-text-field>
          </template>
          <v-date-picker
            v-model="date"
            no-title
            scrollable>
            <v-spacer></v-spacer>
            <v-btn
              text
              color="primary"
              @click="menu = false">
              Cancel
            </v-btn>
            <v-btn
              text
              color="primary"
              @click="$refs.menu.save(date)">
              OK
            </v-btn>
          </v-date-picker>
        </v-menu>
      </div>
      <div style="height:45%;"></div>
      <v-row class="justify-end pe-10">
        <v-btn variant="flat" 
          color="#0097A7"
          class="white--text rounded-pill">
          Save
        </v-btn>
      </v-row>
    </v-card>
  </v-navigation-drawer>
</template>

<script>
export default {
    name: 'AddTaskDrawer',
    props: {
       value: {
        type: Boolean,
        default: false,
      },
    },
    computed: {
      smallScreen() {
        return this.$vuetify.breakpoint.mdAndDown;
      }
    },
    data: () => ({
      drawer: null,
      rules: [v => !v || v.length <= 50 || 'Only 50 characters allowed'],
      weekday: [0, 1, 2, 3, 4, 5, 6],
      type: 'month',
      date: new Date().toISOString().substr(0, 7),
      menu: false,
    }),
    methods: {
      open() {
        this.drawer = true;
      },
      close() {
        this.drawer = false;
      },
    },
    watch: {
       value() {
         if (this.value && !this.drawer) {
        this.open();
      } else if (!this.value && this.drawer) {
        this.close();
      }
    },
    }
  }
</script>
