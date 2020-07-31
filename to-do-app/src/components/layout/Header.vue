<template>
  <div>
    <header class="header">
      <h1>To Do List</h1>
    </header>
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style scoped>
.header {
  background: #333;
  color: #fff;
  text-align: center;
  padding: 5px;
}
.header a {
  color: #fff;
  padding-right: 5px;
}

#nav {
  background: whitesmoke;
}
</style>
