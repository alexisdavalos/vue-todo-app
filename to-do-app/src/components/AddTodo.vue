<template>
  <div class="form-wrapper">
    <form @submit="addTodo">
      <input type="text" name="title" v-model="title" placeholder="Add Todo.." />
      <input type="submit" value="Submit" class="btn" />
    </form>
  </div>
</template>

<script>
import { v4 as uuid4 } from "uuid";
export default {
  name: "AddTodo",
  // component state
  data() {
    return {
      title: "",
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      const newTodo = {
        id: uuid4(),
        title: this.title,
        completed: false,
      };
      console.log(newTodo);
      // Form validation
      if (newTodo.title === "") {
        alert("Field cannot be empty");
      } else {
        // Send up to parent component
        this.$emit("add-todo", newTodo);
        this.title = "";
      }
    },
  },
};
</script>

<style scoped>
.form-wrapper {
  width: 100%;
  margin: 5% 0%;
}
form {
  display: flex;
}

input[type="text"] {
  flex: 10;
  padding: 10px;
  border: none;
  background: whitesmoke;
}
input[type="text"]:focus {
  outline: none;
}
input[type="submit"] {
  flex: 2;
  border: none;
}
</style>
