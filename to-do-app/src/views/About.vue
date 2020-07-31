<template>
  <div class="about">
    <p>This application was built with Vue.js</p>
    <p>You can find the code for this application below</p>
    <a href="https://github.com/alexisdavalos/vue-todo-app" target="_blank"
      >Code Base</a
    >
  </div>
</template>
<style scoped>
.about {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  margin-top: 50px;
}
p {
  margin: 10px;
}
a {
  width: 150px;
  color: white;
  background: #42b983;
  border-radius: 5px;
  font-size: 1.25rem;
  height: 40px;
  margin: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
  text-decoration: none;
}
</style>
