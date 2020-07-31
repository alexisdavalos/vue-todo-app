<template>
  <div
    class="todo-item"
    v-on:click="markComplete"
    v-bind:class="{ 'is-complete': todo.completed }"
  >
    <p>
      <input
        type="checkbox"
        v-on:change="markComplete"
        v-bind:checked="todo.completed"
      />
      {{ todo.title }}
      <button @click="$emit('del-todo', todo.id)" class="del">x</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    },
  },
};
</script>

<style scoped>
.todo-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}
.todo-item p {
  text-align: left;
}
.is-complete {
  text-decoration: line-through;
}
.del {
  background: #e64944;
  color: #fff;
  border: none;
  width: 25px;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
  transition: all 0.25s ease-in-out;
}
.del:hover {
  background: #942622;
}
</style>
