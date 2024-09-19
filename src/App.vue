<template>
  <v-app>
    <v-main class="main-background">
      <v-container class="main-container">
        <ToDoList />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import ToDoList from './components/ToDoList.vue';

export default {
  name: 'App',
  components: {
    ToDoList
  },
  data: () => ({
    //
  }),
}
</script>

<style>
@import '~vuetify/dist/vuetify.min.css';

html, body, #app {
  height: 100%;
  margin: 0;
}

.main-background {
  background-color: #415d43;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.main-container {
  font-family: 'Arial, sans-serif';
  display: flex;
  justify-content: center;
  align-items: center;
  flex-grow: 1;
}
</style>
