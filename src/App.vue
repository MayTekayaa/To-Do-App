<template>
  <v-app>
    <v-layout>
      <v-navigation-drawer
        mini-variant-width="80px"
        class="hidden-md-and-down"
        expand-on-hover
        rail>
        <v-list>
          <v-list-item>
            <v-list-item-avatar>
              <v-img src="./assets/user.png"></v-img>
            </v-list-item-avatar>
            <v-list-item-content>
              <v-list-item-title v-html="`<strong>Foulen Ben Foulen</strong>`"></v-list-item-title>
              <v-list-item-subtitle>foulen.ben.foulen@gmail.com</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
        </v-list>

        <v-divider></v-divider>

        <v-list dense>
          <v-list-item>
            <v-list-item-icon>
              <font-awesome-icon icon="fa-solid fa-list-check" size="lg" />
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title>Tasks</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item>
            <v-list-item-icon>
              <font-awesome-icon icon="fa-solid fa-calendar" size="lg" />
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title>Calendar</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>
      <v-main class="blue-grey lighten-5">
        <Home/>
      </v-main>
    </v-layout>
  </v-app>
</template>

<script>
import Home from './components/Home.vue';

export default {
  name: 'App',

  components: {
    Home,
  },

  data: () => ({
    //
  }),
};
</script>
