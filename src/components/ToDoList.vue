<template>
  <v-container class="todo-container">
    <v-row>
      <v-col cols="12" class="mb-4">
        <v-text-field
          v-model="newTodo"
          label="New To-Do"
          @keyup.enter="addTodo"
          class="field"
        ></v-text-field>
        <v-btn @click="addTodo" class="ml-2">Add</v-btn>
      </v-col>
    </v-row>
    <v-row class="todo-list">
      <v-col cols="12">
        <v-list class="mb-5">
          <v-list-item
            v-for="(todo, index) in todos"
            :key="index"
            class="d-flex justify-space-between align-center"
          >
            <v-list-item-content>
              <v-list-item-title class="listtext">{{ todo.text }}</v-list-item-title>
              <v-list-item-subtitle>{{ todo.date }}</v-list-item-subtitle>
            </v-list-item-content>
            <v-list-item-action>
              <v-btn icon @click="deleteTodo(index)" class="icon">
                <v-icon>mdi-delete</v-icon>
              </v-btn>
            </v-list-item-action>
          </v-list-item>
        </v-list>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      newTodo: '',
      todos: []
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== '') {
        const date = new Date().toLocaleString();
        this.todos.push({ text: this.newTodo, date });
        this.newTodo = '';
      }
    },
    deleteTodo(index) {
      this.todos.splice(index, 1);
    }
  }
};
</script>

<style scoped>
.todo-container {
  background-color: #a5cfa9;
  border-radius: 10px;
  box-shadow: 0 4px 8px #a5cfa9b8;
  padding: 20px;
  max-width: 500px;
  margin: auto;
  min-height: 50vh; /* Ensure minimum height */
  display: flex;
  flex-direction: column;
  justify-content: center;
  overflow-y: auto;
  padding-bottom: 20px; /* Add padding to the bottom */
}
.todo-list {
  flex-grow: 1;
  overflow-y: auto;
}
.mb-4 {
  margin-bottom: 16px;
}
.mb-5 {
  background-color: #8fb996;
}
.ml-2 {
  margin-left: 8px;
  background-color: #8fb996;
}
.field {
  background-color: #8fb996;
  border-radius: 4px;
  margin-bottom: 8px;
}
.icon {
  background-color: #a5cfa9;
}
.ml-auto {
  margin-left: auto;
}

.listtext {
  font-weight: bold;
}

/* Adjust alignment */
.v-list-item {
  display: flex;
  align-items: center;
}

.v-list-item-content {
  flex: 1; /* Takes up remaining space */
}

.v-list-item-action {
  margin-left: 10px;
}
</style>
