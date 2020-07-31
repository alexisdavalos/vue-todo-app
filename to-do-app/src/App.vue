<template>
  <div id="app">
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
// Imports always happen above export and under script tag
import Todos from "./components/Todos.vue";

export default {
  name: "App",
  components: {
    Todos,
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "Todo One",
          completed: false,
        },
        {
          id: 2,
          title: "Todo Two",
          completed: false,
        },
        {
          id: 3,
          title: "Todo Three",
          completed: false,
        },
      ],
    };
  },
  methods: {
    // This method filters the current data object 'todos' and
    // returns an array with the new set of data
    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  font: inherit;
  vertical-align: baseline;
  font-family: "Courier New", Courier, monospace;
}
</style>
