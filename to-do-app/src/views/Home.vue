<template>
  <div id="home">
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
// Imports always happen above export and under script tag
import Todos from "../components/Todos.vue";
import AddTodo from "../components/AddTodo.vue";
import axios from "axios";
import { v4 as uuid4 } from "uuid";
export default {
  name: "Home",
  components: {
    Todos,
    AddTodo,
  },
  data() {
    return {
      todos: [],
    };
  },
  created() {
    axios
      .get(`${process.env.VUE_APP_GET_ROUTE}/?_limit=3`)
      .then((res) => (this.todos = res.data))
      .catch((err) => console.log(err));
  },
  methods: {
    // This method filters the current data object 'todos' and
    // returns an array with the new set of data
    deleteTodo(id) {
      axios
        .delete(`${process.env.VUE_APP_DELETE_ROUTE}/${id}`)
        .then((res) => {
          res.data = this.todos.filter((todo) => todo.id !== id);
          this.todos = res.data;
        })
        .catch((err) => console.log(err));
    },
    // This method adds a new Todo task and simulates an api call
    addTodo(newTodo) {
      const { title, id, completed } = newTodo;
      axios
        .post(`${process.env.VUE_APP_POST_ROUTE}`, {
          title,
          id,
          completed,
        })
        .then((res) => {
          // updates response obj id to avoid key error
          res.data.id = uuid4();
          this.todos = [...this.todos, res.data];
        })
        .catch((err) => console.log(err));
    },
  },
};
</script>

<style>
#home {
  margin: 0 auto;
  width: 90%;
}
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover {
  background: #666;
}
</style>
